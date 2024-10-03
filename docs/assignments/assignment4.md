---
title: Assignment 4 - Alpha
layout: doc
---

# Assignment 4: Back-end Design and Concept Implementation #
In this stage of the development process, I build a database for my app using MongoDB and implement the concepts from Assignment 3

## Data Modeling ##
### Abstract Data Model ###
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
Concept: Homepage[Person, Friends]

States:
friendList: set Friends
connection: friends -> one Person

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
explicit: explicitContent -> one Content
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

### App Definition ###
```
app Haven

```

### Data Diagram ###
![Abstract Data Model Diagram](./abstract%20data%20model.jpeg)

## Concept and Route Implementation ##

### Back-End Github Repo ###
Link to Repo: https://github.com/ashi-kamra/assignment4

### Vercel Deployment ###
Link to Vercel: https://vercel.com/ak118s-projects/assignment4