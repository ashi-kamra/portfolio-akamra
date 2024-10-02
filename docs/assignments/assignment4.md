---
title: Assignment 4
layout: doc
---

# Assignment 4: Back-end Design and Concept Implementation #
In this stage of the development process, I build a database for my app using MongoDB and implement the concepts from Assignment 3

## Data Modeling ##
```
Concept: User //each user in the set of users has 1 username and password

States:
users: set UserType
username: users -> one String
id: users -> one String 

```
```
Concept: Connect[Person]

States: 
connections: set ConnectType
user1: connections -> one Person
user2: connections -> one Person

```
```
Concept: Homepage[Person, Connection]

States:
connections: set ConnectionType
connection: connections -> one Person

```
```
Concept: Message[Content, Sender, Receiver]

States:
messageHistory: set MessageType
message: messageHistory -> one Content
sender: messageHistory -> one Sender
receiver: messageHistory -> one Receiver

```
```
Concept: ConsentSurvey[Content, MessageLog]

States: //need help designing this, cause i think i'm doing it like its OOP...
explicitContent: set ConsentSurveyType
content: MessageLog -> one Content
isExplicit: one Boolean

```
```
Concept: Labelling[Item]

States:
labelledItems: set LabellingType
item: labelledItems -> one Item
label: labelledItems -> one String

```