---
title: Assignment 3
layout: doc
---

# Assignment 3: Convergent Design #
In this stage, I developed the concepts, synchronizations, and wireframes for the app

## Pitch ##
Haven is an app designed to protect. It’s hard nowadays to sustain meaningful relationships and avoid dangerous individuals hidden on social media. This app is made for individuals who want to keep their friends close, and make those friendships even closer.  
By centering the user experience around a select group of connections the user has, users will foster intentional and safe connections. With unique private user id’s, these connections are made only at the consent of both parties, and you are safe from being added by any unwanted users. Haven takes online child sexual abuse seriously, thus safety education, mutual consent, and reporting abuse are central features to the platform. But, we know relationships flourish most when you have fun, so with shared photo boards, message echoing, and podcast rooms, Haven is also a space that preserves. 

## Functional Design ##
**1. Concept: User**

*Purpose:* provides user with authentification and private access to their account.

*Principle* persona representation within the system with a name and system generated id

*State* <br>
`Users: set String, Number` <br>
`username: Users -> one String`<br>
`id: Users -> one Number`

*Action* <br>
`system generateId(out id: Number)` <br>
`register(name: String, id: Number)`

**2. Concept: Connecting[Person, Identifier]**

*Purpose:* establishes access between Persons to communicate

*Principle:* adding 2 identifiers into connector establishes a connection between them. Shows mutual connections between Persons before connecting

*State:*
`Connector: set Identifier`<br>
`Connections: set Persons`<br>
`user1: Connector -> one Number`<br>
`user2: Connector -> one Number`

*Action:*
`system connection(user1: Identifier, user2: Identifier, connector, connections)`<br>
`system mutuals(user1: Identifier, user2: Identifier)`<br>
`cancelConnection(user1: Identifier, user2: Identifier)`

**3. Concept: Homepage[Person, Connection]** 

*Purpose:* a central location to view and access all connections

*Principle:* after creating a connection, homepages are updated to reflect the new connection

*State:*
`Connections: set Person`
`connection: Connections -> one Person`

*Action:*
`system displayConnections(Connections)`<br>
`accessConnection(connection: Person)`

**4. Concept: Messaging[Sender, Receiver]**

*Purpose:* contacting via sending direct messages 

*Principle:* after a sender sends a message, the receiver will receive it

*State:* 
`sender: one Sender` <br>
`receiver: one Receiver` <br>
`message: one Message` <br>
`messageHistory; set Message`

*Action:*
`sendMessage(message: Message, sender, receiver, out messageHistory)`


**5. Concept: ConsentSurvey[Content]**

*Purpose:* manages potentially non-consentually received content

*Principle:* presents options to indicate explicit content was non-consentually received and removes it if necessary

*State:*
`content: one Content`<br>
`isExplicit: Boolean` <br>
`consent: Boolean` <br>
`toRemove: Boolean`

*Action:*
`system scanContent(content: Content, out isExplicit)` <br>
`system survey(isExplicit)`<br>
`indicateConsent(consent, out toRemove)`<br>
`system removeContent(toRemove)` <br>

**6. Concept: Messaging[Sender, Receiver]**
*Purpose:*
*Principle:*
*State:*
*Action:*