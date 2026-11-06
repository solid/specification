# Intent Handover for Solid Applications

## Abstract

This specification defines a mechanism that enables one Solid application to convey user intent to another Solid application. A receiving application MAY use any, all, or none of the conveyed information.

## Status of This Document

This is a draft proposal intended for discussion within the Solid community. It does not yet define a standard and may change based on implementation experience and community feedback.

## 1. Introduction

Solid applications can redirect users to other Solid applications to continue a workflow. During such transitions, the initiating application may already possess information that could simplify the user's experience, such as the user's WebID, Identity Provider (IDP), storage location, or a resource that should be opened.

This specification defines a standardized mechanism for communicating such information between Solid applications.

The mechanism is intentionally non-prescriptive. The receiving application retains complete control over how, or whether, the conveyed information is used.

## 2. Conformance

The key words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** in this document are to be interpreted as described in RFC 2119 and RFC 8174 when, and only when, they appear in all capitals, as shown here.RFC 2119 and RFC 8174.

## 3. Design Principles

The mechanism defined by this specification follows these principles:

* The initiating application MAY provide one or more pieces of contextual information.
* The receiving application MAY use the provided information.
* The receiving application MAY ignore any or all provided information.
* The receiving application remains responsible for validating any information before acting upon it.
* The mechanism does not require any particular authentication or authorization model.

## 4. Intent Parameters

This specification defines intent parameters as either HTTP URL fragment parameters or HTTP URL query parameters. The usage depends on the capabilities of the receiving application.

Receiving applications that run purely in the browser SHOULD use fragment parameters to prevent transmission of information to the server.

Receiving applications that run server side and thus require the intent to be transmitted to the server, MUST use query parameters.

An initiating application MAY include any combination of the following parameters. When multiple intent parameters are present, the receiving application MAY use any subset of them. Query parameter values MUST be URL-encoded according to RFC 3986. Examples in this document omit URL encoding for readability.


| Parameter              | Value                          | Used by intent |
| ---------------------- | ------------------------------ | -------------- |
| `intent`               | login, open                    |                |
| `solidWebId`           | A Solid compatible WebID URI   | login          |
| `solidIdp`             | A Solid Identity Provider URI  | login          |
| `solidStorage`         | A Solid Storage URI            | open           |
| `solidResource`        | Resource URI (one or multiple) | open           |


### 4.1 Intent

This parameter signals the intent of the user to the receiving app. Currently two possible values are specified.

### 4.1.1 login

When this intent is signalled, the receiving application MAY initiate authentication using the supplied values from either `solidWebId` or `solidIdp`

Examples using fragment parameters:

```
https://target.app/#intent=login&solidWebId=https://example.com/profile/card#me
```

Examples using query parameters:
```
https://target.app/?intent=login&solidWebId=https://example.com/profile/card#me
```
### 4.1.2 open

When this intent is signalled, the receiving application MAY use the provided values from `solidStorage` and/or `solidResource` to start the application with a specific resource.
The initiating application can implement 'open with...' using this mechanic.

Examples using fragment parameters:

```
https://target.app/#intent[]=open&solidResource=https://storage.example.com/resource.ttl
```

Examples using query parameters:
```
https://target.app/?intent[]=open&solidResource=https://storage.example.com/resource.ttl
```

### 4.2 WebID

A WebID identifying the user.

Examples using fragment parameters:

```
https://target.app/#solidWebId=https://example.com/profile/card#me
```

Examples using query parameters:
```
https://target.app/?solidWebId=https://example.com/profile/card#me
```

A receiving application MAY use this value to initiate authentication for the supplied WebID.

### 4.3 Identity Provider (IDP)

The URI of an Identity Provider.

Examples using fragment parameters:

```
https://target.app/#solidIdp=https://idp.example.com/
```

Examples using query parameters:
```
https://target.app/?solidIdp=https://idp.example.com/
```

A receiving application MAY use this URI as a suggested Identity Provider for authentication.

### 4.4 Storage URI

The URI of a Solid storage location.

Examples using fragment parameters:

```
https://target.app/#solidStorage=https://storage.example.com/
```

Examples using query parameters:
```
https://target.app/?solidStorage=https://storage.example.com/
```

A receiving application MAY use this value as the preferred storage location. For users that have multiple storage locations in their profile information, this parameter conveys which storage location the initiating application intends the receiving application to use.

### 4.5 Resource URI

The URI of one or multiple resources. If multiple resources are to be opened, this parameter can be used multiple times.

Examples using fragment parameters:

```
https://target.app/#solidResource=https://storage.example.com/documents/report.ttl
https://target.app/#solidResource[]=https://storage.example.com/documents/report.ttl&solidResource[]=https://storage.example.com/documents/report-metadata.ttl
```

Examples using query parameters:
```
https://target.app/?solidResource=https://storage.example.com/documents/report.ttl
https://target.app/?solidResource[]=https://storage.example.com/documents/report.ttl&solidResource[]=https://storage.example.com/documents/report-metadata.ttl
```

A receiving application MAY attempt to open, inspect, or otherwise use the referenced resource as appropriate for the application's functionality.

## 5. Extensibility

Future versions of this specification MAY define additional intent parameters.

Applications SHOULD ignore parameters they do not recognize unless another specification defines their semantics.

Future versions of this specification may evolve towards a broader audience, as the mechanic as described by this specification is not unique to Solid as an ecosystem.
