---
title: Assignment 6
layout: doc
---
# Assignment 6 - User Testing and Review #
In this final assignment, I will test my app out with selected users to evaluate how they interact with the app and whether their needs were met and whether my design goals were implemented well.

## Pre-populated Data ##
Because Haven is a direct messaging social media app, the only pre-populated data I can include is existing users for them to connect with. Thus, I added 5 dummy users for the user to connect with and message.

## Task List ##
| Title | Instruction | Reasoning |
| ------ | ------ | ----- |
| Register | User will register a new account with the app | This is a prequisite action to all other functions in Haven |
| Connect | User will make a connection with another existing user in the app | Connecting with friends online is a central feature as Haven is a social media app who goal is to strengthening existing friendships. I hope to learn whether users will feel like connection is a more complex process then on normal social media platforms, as that was intended for safety concerns. |
| Message | User will send a message and will respond to a message received by that new connection | Because Haven is a DM social media app, messaging is one of the central feature that must be tested to see if its functional, and is Discoverable (in terms of Usability heuristic), as that was the intention behind the implementation. | 
| Update username | Users will change their username to a new username by inputting this information to the app | Again, i'd like to test the Discoverability of this feature, and see if they understand the principle that you aren't meant to change your id. |
| Navigate | Users will navigate around the app, clicking different links to take them to different pages | I want to see if the users feel like the app is consistent in its linguistic heuristics, and also error tolerant if they click the wrong link. |
| Access Id | User will attempt to click a button in order to view their unique private id. | I want to test the error tolerance of this feature, and Fitt's law, to see if it is too easily reachable, as that would undermine intentions about safety.|
| Logout/in | Users will log out of the app, and input the necessary information to try and log back in | Similar to testing connection, users should feel as though logging in and out is more complex/tedious, and will be deterred from it for safety thus testing the Discoverability heuristic.|


## User Test #1: Mei Brunelle ##
I conducted my first user test of Haven with Mei Brunelle, a junior at Wellesley College. When she sat down and noticed the homepage, she joked “It’s already broken isn’t it…”, in reference to the “Loading…” message on the screen after which nothing loaded. But, she quickly moved on and got started on the tasks. 
<br>
<br>
Many of the tasks, like Register, Update Username, and Message, she completed quickly and easily. She navigated to the correct pages with ease, and seemingly a sense of familiarity. Indeed, after asking how she knew which pages to navigate to or what buttons to press, she mentioned how either there were clear written instructions (like “Click to see your id”) or the layout was very similar to other platforms she’d used before, like iMessages, and thus she relied on her intuition for what actions to take. 
<br>
<br>
Her main pain points were with the Connecting and Login functions, specifically in regards to the long, complex unique id assigned to each user. Once or twice, when attempting to connect with a user by inputting their id into the connector, she inputted the id incorrectly and had to retry to get it right. In her words, “I felt like I could mess that up often.” In a similar vein, after logging out, Mei realized that she did not remember or write down her own private id, and could not log back into the account, saying “Well, that’s not good.” Within the gulf of execution, Mei knew what she needed to do, but did not have the means to do so. 
<br>
<br>
On the whole, however, Mei enjoyed using the app. She thought the colors, the font, and the lack of a follower count contributed to a “very calming” experience. She also thought it felt alot like MySpace, or “retro” social media apps. 

## User Test #2: Annie Chen ##
My second user test of Haven was conducted with Annie Chen, another junior at Wellesley College. When given the first task to Register, she navigated to the login page, but hesitated between whether she should use the login component or the register component. After choosing to register, she entered her information and successfully registered but was also unsure (similar to mei) whether the task was completed or not due to the “Loading…” message. 
<br>
<br>
The connecting and messaging tasks were quite easy for her, which she attributes to the clear situational context, and information scent through the use of the borders, or underlined text. “It was pretty straightforward.”
<br>
<br>
Her main pain points came from the Update username and Login/logout tasks. When attempting updating her username, she misnavigated, and was unsure where to complete this task. After she managed to get there, updating it was simple and quick. According to Annie, she thought “Settings” and “Connector” were one page, and thus didn’t immediately think to go there. With Login/out, she encountered the same problem as Mei, and accidentally logged out before she wrote down or fully remembered her id. Without prompting, she decided to register another account, and write down the id of that one for future reference. Once again, within the gulf of execution, Annie knew what she needed to do, but did not have the means to do so. 
<br>
<br>
In general, Annie also enjoyed using Haven. She mentioned that after doing the other tasks, she was able to pick up on the functionality of the app easily, which suggests high learnability. She specifically how she appreciated that the id was automatically generated for you, and through that interface and font choice was nice. In her words, “It was overall very intuitive.”

## Opportunitites for Improvement ##
*1. Login Functionality* (Conceptual)
- When testers logged out, they often did not have the input to log back in. 
- Occuring because they did not remember it (because it's system generated), or they did not write it down
- One improvement could be to make an alert when users attempt to log out, that they cannot log back in without their id.

*2. Loading Message* (Linguistic)
- When users registered, they often were confused as to if the task was complete
- Occuring because of a loading message on the homepage that made them expect something else
- One improvement could be to change that message to "You have no connections." Or something more informative and less misleading.

*3. Navigation Clarity* (Physical + Linguistic)
- When users attempted to navigate, there was some lack of clarity about which pages would lead to which functions
- This is because the page links were spaced too close together and looked like one word
- One improvement could be using distinct symbols instead of text to label the settings page, or to have it on a different side of the nav bar to make it more distinct.