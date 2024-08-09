# W3C Solid Community Group: Implementer Feedback

* Date: 2024-08-07T12:00:00Z
* Call: https://meet.jit.si/solid-cg
* Chat: https://matrix.to/#/#solid_specification:gitter.im
* Repository: https://github.com/solid/specification
* Status: Published


## Present
* [Virginia Balseiro](https://virginiabalseiro.com/#me)
* [elf Pavlik](https://elf-pavlik.hackers4peace.net)
* [Sarven Capadisli](https://csarven.ca/#i)
* [Rahul Gupta](https://cxres.pages.dev/profile#i)
* [Graham Williams](https://solidcommunity.au/)
* Kelly O
* Sergio J. Rodriguez Mendez
* Jesse Wright
* Erich Bremer
* [Michal](https://id.mrkvon.org)
* Anushka

## Announcements

### Meeting Guidelines
* [W3C Solid Community Group Calendar](https://www.w3.org/groups/cg/solid/calendar).
* [W3C Solid Community Group Meeting Guidelines](https://github.com/w3c-cg/solid/blob/main/meetings/README.md).
* No audio or video recording, or automated transcripts without consent. Meetings are transcribed and made public. If consent is withheld by anyone, recording/retention must not occur.
* Join queue to talk.
* Topics can be proposed at the bottom of the agenda to be discussed as time allows. Make it known if a topic is urgent or cannot be postponed.

### Participation and Code of Conduct
* [Join the W3C Solid Community Group](https://www.w3.org/community/solid/join), [W3C Account Request](http://www.w3.org/accounts/request), [W3C Community Contributor License Agreement](https://www.w3.org/community/about/agreements/cla/).
* [Solid Code of Conduct](https://github.com/solid/process/blob/main/code-of-conduct.md), [Positive Work Environment at W3C: Code of Ethics and Professional Conduct](https://www.w3.org/Consortium/cepc/)
* Operating principle for effective participation is to allow access across disabilities, across country borders, and across time. Feedback on tooling and meeting timing is welcome.
* If this is your first time, welcome! please introduce yourself.


### Scribes
* Virginia Balseiro
* elf Pavlik

### Introductions

* 
---

## Topics

### Graham Williams - Solid Community AU

URL: https://solidcommunity.au/

* GW: We are working with health data, closely cooperating with the government. Our health data is all over the place, imagine how much more benefits we will get if we had it all in one place.
* GW: Project Ecosysl looks into implications of distributed data for machine learning. Work covers data science, ML, pirvacy in ML context, how to build ML models with massively federated data. 
* GW: Focus on individuals as owners of the data; become better informed; having a single location for all their data. An important thing is pipelines to ingest data into pods. 
* GW: We've been focused on privacy, last couple of years more in th context of Solid Pods. In the early days we were looking for the "killer app" to get the message across. It was hard to sell the message without concrete examples. We have developed a number of simple apps to highlight/demonstrate the concept. It is much more powerful to be able to have something to demonstrate. One of the first ones was PodNotes, very simple note taking app. We're a software engineering oriented organization. We use Flutter for all our work. Solid is not particularly well supported in that platform. We've focused on open source, getting what we learn into four packages for Flutter. 
* GW: For all of these apps, a nice feature of Flutter is it's platform agnostic. Many of these apps have a link to a deployment on our Solid Community Server. 
* GW: With our packages you an build a Solid app with Flutter fairly quickly. One of my colleagues wrote CVPod in a few days. It takes any CV data, publications, etc. in your pod. 
* GW: Indigenous communities in Australia tend to be underprivileged and have serious health problems. Really need to take a different approach to delivering healthcare to the community. We were invited by Gurriny Yealamucha health services to explore how to give memebrs of the community confidence in sharing their health data. Because of the colonization history there is deep mistrust of governemnt telling the commjunity what they should do. The idea is giving them confidence that they have control of their health data. More than health data - also lifestyle data that can be shared with the clinic and aids in helping the individuals. We have developed a number of apps for them. Patient App has been deployed. One of the big parts of this project is how to populate pods with existing data. 
* GW: We have a pipeline from the health information system feeding data into the individual's pods. They can look at this data, future appointments, prescriptions, record of blood pressure readings, etc. All of that is pushed into the pod. They can monitor other social activities that impact upon their diabetes for example. 
* GW: The Clinic app gives an overview of the whole community to doctors. Care Coordination Team App gives info to coordinators. Clinic can access any data the patients have shares, collect data on behalf of the patient, etc. These two are less developed, we're more focused on the Patient App. This has been rcently rolled out to patients (past month) and we're getting feedback from the community to make sure we're focusing on what they want and need. 
* GW: We're looking into how to use pods to support medican clinical trials. Participants have the right to pull themselves our of clinical trials. We're experimenting with these concepts, working with a Berlin based manufacturer of medical devices. We're looing at patients involved in clinical trials to test these devices and be surveyed on their interactions with the devices. The first phase in trial now is using BrightStim2. It supports patients suffering from depression. It's a helmet that can read EEG signals and send moderate pulse signals, non-invasive tool. That data is stored on their pods. Researches have been given permission to access that data and potentially give feedback from their analysis. Eventually perhaps models can be built to ??? feedback into the pod. 
* GW: Followup project is looking into next generation of these devices. 
* GW: We have been developing a number of student apps from students in the university. This one is an example, SecureDiaLog, is like a diary of blood pressure, heart rate, weight, focused on diabetes, and allows the individual to visualize that data. 
* GW: These are all with the goal of getting the story of pods out there. One question would I want to put health data in my pod. I'd be happy to do that if I am sur ethat data is only accessible to me and only shared with others if I say so. Quite  abit of our focused is around the principle of TNO (Trust No One). We've been implementing a system where all the data put into our pods is encrypted, and none is ever decrypted. It is only decrypted once it's on device. You lose the ability to link this data, but it's been an important part of what people want in the project and gives us assurance that we're collecting very private data from our indigenous community, we would not want our servers to be breached and all their data. 
* GW: Challenges: data pipelines is an issue for the whole concept of pods. How to get all this data from all these sources into pod. Data security, the limitation of our TNO approach is that it can only be decrypted on the device. The other area is once we share data to other pods and then decide not to, what's the mechanism to retrieve what we already shared. The other challenge is ML with federated. 

#### Q&A

* eP: Exciting to learn more about this work. I'm focused on interop between apps. If the data is not encrypted, would the notes taking app have access to health data of the user?
* GW: Encryption is optional. We turned it on by default but any app depending on the developer might choose to encrypt some parts and not others. Any other apps you develop must adhere to which parts are encrypted. 
* eP: If data is not encrypted would note taking app have access or is there a way to scope that data? My notes app should not have access to my health data, etc. 
* GW: We had recent discussion on that. We thought about having different encryption keys for each app rather than single key for the whole pod. In our current implementation we decided to use a single key for encrypting across all of our data stores within a pod, on the thinking that it's the same user accessing the data. Maybe we'll be whitelisting apps to access particular data as a way to limit scope, but we're not well developed in the thinking of scopes. 
* A (on Jitsi chat): At the moment yes, if the data is not encrypted within an app, another app can access that data. We haven't particularly looked at that type of authorisation mechanisms yet. 
* eP: Best place to follow up for more questions? 
* GW: Happy to arange another time where we can chat. 
* RH: what server are you using?
* GW: CSS. We've evolved with CSS over the last couple of years. 

### Sarven Capadisli - dokieli
URL: https://dokie.li/

* SC: Project site: https://dokie.li/
* SC: Source code: https://github.com/linkeddata/dokieli
* SC: History: https://csarven.ca/okieli-dokieli
* SC: dokieli is a socially-aware clientside editor for decentralised article publishing, annotations and social interactions with an ocean of open web standards at its disposal.
* SC: It resembles the first browser [WorldWideWeb](https://en.wikipedia.org/wiki/WorldWideWeb) and [Amaya](https://www.w3.org/Amaya/), a desktop web browser and editor that was developed by W3C from 1996-2012 to provide a framework for experimenting with and validating web specifications. 
* SC: I built what I needed, and use it (still).
* SC: Generally speaking publishing, editing, annotating Web documents is arguably the most common use case on the Web since the beginning.
* SC: Intended to create and edit any kind of article, including reviews and assessments, technical specifications, news, social media posts, and even slideshows. And annotations and notifications in/around that.
* SC: Something resembling dokieli started back in 2011 to somewhat of a reaction to research communication on the Web. Shortly after the aimed to cover various kinds of articles and annotations. Making sure everything is [based on open standards](https://github.com/linkeddata/dokieli/blob/main/README.md#specifications), without compromising on human- and machine-readability. See some [screencasts](https://github.com/linkeddata/dokieli/blob/main/README.md#screencasts).
* SC: Keeping [Authoring Tool Accessibility Guidelines](https://www.w3.org/TR/ATAG/) and [Web Content Accessibility Guidelines](https://www.w3.org/TR/wcag-3.0/) and other related works and initiatives at W3C in mind, dokieli is in a way how we can meet those needs and guidelines within a Solid (or alike) environment.
* SC: Solid Protocol is among many other specifications that's needed to realise something like dokieli - authoring/annotation/notification tool.
* SC: One of the shortcomings in the Solid ecosystem is that we don't talk much about accessibility, both making sure Solid apps are accessible as well as the generated content is accessible. AFAICT, most Solid apps are not even remotely generating accessible content (as far as W3C guidelines goes). If we're cutting corners on what the current web is expecting or making it difficult to develop authoring tools because of technical decisions in Solid, we're diverging from the main story (of the Web), ethical Web principles - "the web is for all people" etc. There will be a major hurdle for adoption if we don't tick those boxes. A bit like shooting ourselves in the foot. Of course security and privacy for instance are equallty important. https://www.w3.org/ right at the top mentions "accessibility" and it has been at its core since early on.
* SC: dokieli helped people to understand the core concepts and connect the dots underlying Solid for instance, and broadly about decentralisation, making use of own identity and web space and so forth.
* SC: Shared this work with many individuals and communities over the years, in workshops and talks at conferences and research labs etc.
* SC: Over the years, dokieli in essence was a way of "eating our own cooking" in the context of *open* specification development: https://csarven.ca/self-review-chairing#dokieli-qa-spec-development . Again, see links to standards and screencasts linked above as example.
* SC: Briefly on funding: various research/education institutions over the years by supporting talks/workshops/presentations,  research and develpoment at MIT/Crosscloud (2015-2016) - output into Solid development and Social Web WG, Web Annotation WG etc., NLNet (2024), and more in the pipeline. Will let everyone know when okay to share publicly.

#### Q&A 

* RG: Comment on accessibility: one of the issues with accessibility is let's have some tags and let's ??? I like the use of the word ??? Somebody who is blind have different needs from other disabilities. You need a way to have different kind of user interfaces, the infrastructure you have in dokieli will still be reused across those user interfaces. Is there a path in the development of dokieli that could help that happen? 
* SC: I don't think the apporach in dokieli is applicable or ideal for different use cases or needs. It's not for photo sharing, for instance. Something like accessibility guidelines is applicable for a photo app but generated content is a bit different. dokieli is focused on prose content for the most part. Articles, blogposts, etc. Accessibility expectations are different. If the question is about authoring tools, we can have our cake and eat it too if we rely on existing formats like HTML as a generated content, because it has proven itself. We have 35 year track of it working. It's the lingua franca of the web. We need to separate data from UI but something like dokieli is not just embedding JS on HTML, but you can use it as a browser extension. That's how you can annotate any type of article and store the annotation on your own storage. We can annotate the whole web using dokieli in a Solid environment. Blocking those possibilities is shooting ourselves in the foot. People want to have interactive documents on the web, and some efforts in Solid are not acknowledging these and making it impossible to continue. If we go on that direction solid is not an extension of a web, but a fork based on who shows up. 
* SC: Likewise with authorization, users have mental models and if we move that to a separate authorization app, that's more mental load and we lose them. Basic UX patterns - with lest resistence and making things intuitive - in contrast to requiring them to completely change their behaviour. No one cares about the underlying tech. People want to click buttons and get on with their needs. Take GDocs as example. Their design to share an article comes after a lot of research and testing. It is a much harder sell to tell people to stop doing that kind of a thing and do this other thing. At that point we'd lose them. Again, there is long history of UX design patterns here.
