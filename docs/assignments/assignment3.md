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
`Users: set String, Number`
`username: User -> one String`
`id: user -> one Number`

*Action* <br>
`system generateId(out id: Number)`
`register(name: String, id: Number)`