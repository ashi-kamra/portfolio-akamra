---
title: Assignment 4 - Beta
layout: doc
---
# Assignment 4: Final Back-end Design and Concept Implementation #
In this stage of the development process, I build a database for my app using MongoDB and implement the concepts from Assignment 3

### Back-End Github Repo ###
Link to Repo: https://github.com/ashi-kamra/assignment4

### Vercel Deployment ###
Link to Vercel: https://assignment4-five-sooty.vercel.app/

## Design Reflection and ChatGPT Kudos ##
This final implementation of our concepts into the back-end allowed me to refine my ideas alot, based on our time constraints and based on how our concepts could interact with one another.

In my ConsentSurvey concept, I originally didn't have a set storing data, but while implementing I realized that it would be a good idea to store content that was labeled as explicit for future usage (like collaborating with law enforcement). 

I also faced the decision of whether I wanted to make labels unique in my Labelling concept, and I decided that a user may have multiple labels of the same kind but with different connections, so it was unnecessary for them to be unique and limits users ability.

My last major decision decision was determining how to implement an automatic consent survey, where the system would automatically, continously scan messages and present users with the survey when it encounters what it deems to be explicit. But, sadly, I don't have enough time to implement this or the knowledge of how to do it, so I changed the concept to be one in which users can indicate whether or not they received this message non-consentually themselves. I do think this adds some user agency and additional privacy for them, so its not a horrible trade-off.

I used ChatGPT in this project to:
1. Help figure out how to generate random user id with uuid
2. Determine difference between async and await functions
3. Better understand mongoDB query notation and $and/or keywords

