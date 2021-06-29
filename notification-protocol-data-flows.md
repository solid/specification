# Notification Protocol Data Flows

Created: 2021-02-12

Modified: 2021-06-29

Authors: Aaron Coburn, Jack Lawson

License: MIT License

Copyright: Inrupt, 2021

Status: Editor’s Draft


This document describes the client/server protocol for negotiating and establishing a connection for reacting to Solid notifications. This does not define the content of those notifications, though some discussions have suggested that the messages could use Activity Streams (JSON-LD) format.

## 1. Gateway discovery

A client looks for the gateway URL in the /.well-known/solid document:

```
request ->

GET /.well-known/solid

<- response

Content-Type: application/json
{
  "notificationGateway": "gateway URL"
}
```

## 2. Protocol negotiation

A client interacts with the gateway to negotiate which protocol to use, based on the supported protocols available and the required feature set requested. Any features listed in the "features" property should be considered required in the protocol selection. No authentication is required at this endpoint. The “features” names are included merely as examples.

```
request ->

POST {gateway URL}
Content-Type: application/json
{
    "protocols": ["ws", "sse", "webhook"],
    "features": ["state", "ttl", "rate"]
}
```

The response will include the selected protocol, the endpoint for negotiating a connection and the supported features offered by that protocol.
```
<- response

Content-Type: application/json
{
    "endpoint": "https://notifications.example/",
    "protocol": "ws",
    "features": ["state", "ttl", "rate", "foo", "bar"]
}
```

A complete list of features should be defined somewhere, similar to how IANA manages such definitions. An initial list could include:

**state:** The protocol supports sending notifications based on a last known state. If the provided state does not match the current state of the topic, the most recent notification will be delivered immediately (rather than waiting for the next update).
**ttl:** The protocol supports requests to control the length of time in seconds determining how long a connection will last
**rate:** The protocol supports controlling the rate of message delivery such that there is a minimum amount of time in seconds between notification delivery
**filter:** The protocol supports filtering messages based on RDF triple patterns




## WebSocket negotiation
### 1. Notification endpoint negotiation

Once a protocol has been selected, send any connection-specific details. This is also where any  authorization enforcement happens. A “topic” parameter is required for every endpoint. Other parameters will be derived from the supported features and may or may not be required, depending on the protocol itself.
```
request ->

POST {"endpoint" URL}
Authorization: DPoP <token>
DPoP: <proof>
Content-Type: application/json
{
    "topic": "https://pod.example/resource",
    "state": "opaque state",
    "ttl": "max length of connection",
    "rate": "10"
}
```
The response will be protocol-specific and will contain information about making the connection to the endpoint. For browser-based protocols, this response may include a Cookie that will be used for authentication. That Cookie could be a signed/encrypted JWT with the negotiated feature data or it can be entirely opaque, connecting to a session store on the server, but that would be an implementation choice. As described in this example, the Cookie would need to be scoped to the same domain as the notification endpoint itself.

Instead of a cookie, the response could include a one-time authentication code in the endpoint URL.

The {client} portion of the path allows us to scope cookies to particular client identifiers. The nonce should be used to prevent malicious apps from re-using cookies that they shouldn’t be using. An invalid nonce value, for instance, would cause the WS connection to fail.

The entire endpoint URL should be treated as opaque by a client.

Three implementation patterns for handling auth include:
Use cookies with names scoped to client identifiers and opaque values that map to a session database. That database would contain the various feature values (topic, state, etc) so that the client connection will know which topic to listen to.
Use cookies with names scoped to client identifiers and an encrypted JWT as a value. This avoids the use of a server-side database and instead relies on the encrypted JWT to manage the connection details of a client. (ESS will likely implement this)
Do not use cookies but rather supply a one-time access code in the endpoint URL

```
<- response

Content-Type: application/json
Set-Cookie: key=value; Secure; HttpOnly
{
    "protocol": "ws",
    "endpoint": "wss://notifications.example/?auth=Ys3KiUq"
    "subprotocol": "solid-0.3"
}
```
### 2. Protocol-specific notification endpoint connection
```
javascript ->

const ws = new WebSocket(endpoint, subprotocol)
```
The Cookie from the previous step is sent here. When a connection is dropped or interrupted, a client should re-start this flow at step 1 of the WebSocket negotiation flow.

Open Questions
When writing a WebSocket server, one would typically include the name of a “Subprotocol”. The legacy WebSocket design uses the string “solid-0.1” for this subprotocol. The ESS implementation supports both “solid” and “solid-0.2”, but we should define this string. One recommendation is to use a domain identifier in order to avoid name conflicts. That said, one cannot include slash (/) characters in this identifier, so a URL cannot be used here.
When a WebSocket connection is terminated, a “CloseCode” is returned to a client. We can define these codes for Solid. The 4xxx range of integers is available for our use. Some background on this includes RFC 6455, IANA and the CloseEvent WebAPI. In the ESS implementation, the following close codes are used: 4400 (Invalid topic), 4401 (Unauthorized) and 4402 (Invalid Subprotocol). The string “reason phrases” could be IRIs.



## EventSource Negotiation
EventSource interactions are nearly identical to WebSocket interactions. The differences are principally in the JavaScript APIs that are used and the absence of a “subprotocol” in the EventSource negotiation. Implementations are free to support different features within these protocols.
### 1. Notification endpoint negotiation
```
request ->

POST {"endpoint" URL}
Authorization: DPoP <token>
DPoP: <proof>
Content-Type: application/json
{
    "topic": "https://pod.example/resource",
    "state": "opaque state",
    "ttl": "max length of connection",
    "rate": "30"
}
```
```
<- response

Content-Type: application/json
Set-Cookie: key=value; Secure; HttpOnly
{
    "protocol": "sse",
    "endpoint": "https://notifications.example/"
}
```
### 2. Protocol-specific notification endpoint connection
```
javascript ->

const sse = new EventSource(endpoint, {"withCredentials": true})
```
The cookie from the previous step is sent here. When a connection is dropped or interrupted, a client should re-start this flow at step 1 of the EventSource negotiation flow.




## WebHooks Negotiation

### 1. WebHook endpoint negotiation
```
request ->

POST {"endpoint" URL}
Authorization: DPoP <token>
DPoP: <proof>
Content-Type: application/json
{
    "topic": "https://pod.example/resource",
    "target": "https://receiver.example/HeCsII8wbhaL7",
    "ttl": "max length of connection",
    "rate": "60"
}
```
```
<- response

Content-Type: application/json
{
    "protocol": "webhook",
    "expires": "datetime",
    "target": "https://receiver.example/HeCsII8wbhaL7",
    "endpoint": "https://notifications.example/Wk8CwhaqPm"
}
```
### 2. Protocol-specific notification endpoint connection
```
request ->

GET {"endpoint" URL}

<- response

Content-Type: application/json
{
    "protocol": "webhook",
    "expires": "datetime",
    "target": "https://receiver.example/HeCsII8wbhaL7",
    "endpoint": "https://notifications.example/Wk8CwhaqPm"
}
```
```
request ->

DELETE {"endpoint" URL}
```
```
<- response

204 No Content
```



## Linked Data Notifications Negotiation
LDN interactions are nearly identical to those of Web Hooks. The difference is principally around the use of “target” for WebHooks and “inbox” for LDN.

### 1. Notification endpoint negotiation
```
request ->

POST {"endpoint" URL}
Authorization: DPoP <token>
DPoP: <proof>
Content-Type: application/json
{
    "topic": "https://pod.example/resource",
    "inbox": "https://receiver.example/inbox/",
    "ttl": "max length of connection",
    "rate": "300"
}
```
```
<- response

Content-Type: application/json
{
    "protocol": "ldn",
    "expires": "datetime",
    "inbox": "https://receiver.example/inbox/",
    "endpoint": "https://notifications.example/nYDd7HxsRRz"
}
```

### 2. Protocol-specific notification endpoint connection
```
request ->

GET {"endpoint" URL}
```
```
<- response

Content-Type: application/json
{
    "protocol": "ldn",
    "expires": "datetime",
    "inbox": "https://receiver.example/inbox/",
    "endpoint": "https://notifications.example/nYDd7HxsRRz"
}
```
```
request ->

DELETE {"endpoint" URL}
```
```
<- response

204 No Content
```
