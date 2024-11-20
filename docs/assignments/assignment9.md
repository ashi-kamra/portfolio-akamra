---
title: "Project Phase 3: Convergent Design"
layout: doc
---
# Project Phase 3: Convergent Design

## Conceptual Design

### Concepts ###

1. **Concept:** Grouping
   - **Purpose:** allows a collection of invited users to come together and complete intended tasks
   - **Operational principle:** An organizer creates a group and invites specific users to join, who can complete actions like pooling money, track the transactions of money, and run a lottery to distribute the money.
   - **State**
     - groups: **set** Group
     - name: groups -> **one** String
     - owner: groups -> **one** User
     - members: groups -> **set** User
     - currentValue: groups -> **one** Integer
     - cycleStartDate: groups -> **one** Date
     - cycleDuration: groups -> **one** Integer
     - contributionFrequency: groups -> **one** Integer
     - contributionAmount: groups -> **one** Integer
     - currentRound: groups -> **one** Integer
   - **Actions**
      ```
        create()
        disband()
        addMember()
        removeMember()
        getMembers()
        getGroup()
        getOwner()
        getCurrentRound()
        setCurrentRound()
        getContributionFrequency()
        setContributionFrequency()
        getContirbutionAmount()
        setContributionAmount()
        contribute()
        disburse()
      ```
2. **Concept:** Permissioning
   - **Purpose:** Allows users to vary the content they have access to based on a set of permissions
   - **Operational principle:** Users can either be organizers and members. Organizers have all the permissions of a member, with additional features like creating a group, etc.
   - **State:**
     - organizers: **set** User
     - members: **set** User
   - **Actions:**
      ```
        addMemberPrivileges(u: User)
        addOrganizerPrivileges(u: User)
        getRoles(u: User)
      ```
3. **Concept:** Scheduling
   - **Purpose:** 
   - **Operational principle:** 
   - **State:** 
        - times: **set** UserTime
        - userTime: **set** Strings
        - start: userTime -> one Date
        - end: userTime -> one Date
        - member: userTime -> one String
     
   - **Actions:**
      ```
      addAvailability(s: one Date, e: one Date, user: one String)
            create userTime with start, end, and user
            add userTime to times
    
      removeAvailability(user: one String, block: one userTime)
            search for block within times
            if userTime matches block
            remove that userTime from times

      changeAvailability(s: one Date, e: one Date, block: one userTime)
            find userTime in time that matches block
            edit start to s and end to e
        
      ```
4. **Concept:** Notifying
   - **Purpose:** to convey a time-sensitive matter requiring action in a brief, temporary message to a set of recipients
   - **Operational principle:** users can notify other users about emergencies or send reminders about upcoming meetings or payments, and curate the message specifically
   - **State:**
     - notifications: set NotificationType
     - message: notifications -> one String
     - sender: notifications -> one User
     - recipients: notifications -> set User
     - actionType: notifications -> one ActionType (like Payment Reminder or SOS Alert)
     - deadline: notifications -> one DateTime
     - group: notifications -> one Group

   - **Actions:**
      ```
        createNotification(sender: one User, message: one String, recipients: set User, actionType: one ActionType)

        sendNotification(notification: one NotificationType)

        notifyPaymentDue(sender: one User, group: one Group, amount: one Integer, deadline: one DateTime)

        triggerSOSAlert(sender: one User, group: one Group, message: one String)

      ```
5. **Concept:** Messaging
   - **Purpose:** Users can converse with each other via text messages.
   - **Operational principle:** After a message is sent from a sender to a recipient, the recipient can read the message until it is deleted.
   - **State:**
     - messages: set Message
     - sender: Message -> one User
     - recipient: Message -> one User
     - content: Message -> one String
     - inbox: User-> set message
     - status: Message -> one Status (Status = {unread, read, archived})
   - **Actions:**
      ```
        send (sender: User, recipient: User, content: String, out message: Message)

        read (recipient: User, message: Message)
         
        delete (recipient: User, message: Message)

        archive (recipient: User, message: Message)

      ```

### Dependency Diagram
![Dependency Diagram](./Dependency%20Diagram.jpeg.jpeg)

### Synchronizations
```
app Oscar
	includes User, Authenticating, Sessioning, Messaging, Permissioning, Notifying, Grouping, Scheduling

	sync register (username, password: String, out user: User)
Authenticating.register (username, password, user)

sync login (username, password: String, out user: User, out session: Session)
Authenticating.authenticate (username, password, user)
Sessioning.start (user, session)

sync authenticate (session: Session, out user: User)
Sessioning.getUser(session, user)

sync logout (session: Session)
Sessioning.end (session)

sync createMeeting(session: Session, group: Group, start: one Date, end: oneDate):
	Grouping.getGroup(group)
owner = Grouping.getOwner()
	Scheduling.setDateLimits(owner, start, end)

sync addMeetingTimes (session: Session, group: Group, date: one Date, availability: one Boolean):
	Grouping.getGroup(group)
	Scheduling.addAvailability(date, availability, user)

sync chooseMeetingTime (session: Session, group: Group, times: set UserTimes):
	Grouping.getGroup(group)
	owner = Grouping.getOwner()
	Scheduling.chooseTimes(owner, times)

```


## Visual Design Study
[Link to slides](https://docs.google.com/presentation/d/1Quqzt2-apsNIZY8JpYUU5dHNnswlzgmrzjgr9w5SKcY/edit?usp=sharing)

## Wireframes
[Figma link](https://www.figma.com/proto/MVGBqp7x2k5w4ne2zxCgS1/6.1040-Oscar-Prototype?node-id=9-4&node-type=canvas&t=K10lI56XIkc2Bq7r-1&scaling=scale-down&content-scaling=fixed&page-id=0%3A1&starting-point-node-id=9%3A4&show-proto-sidebar=1)

## Heuristic Evaluation
#### Usability
**Discoverability:** 
Observation 1: The use of clear labels like "Create an Account," "Login", "Organize a ROSCA group", "Join a ROSCA group as a Member," and "Schedule a Meeting" makes it straightforward for users to understand what actions are available. It supports the heuristic by offering clear entry points for key tasks. <br>
Suggestion: we could introduce brief explanatory texts that appear when the user hovers over items, i.e., for buttons that need to be clarified in meaning. <br>
Tradeoff: Adding more explanatory text or visual aids could slightly clutter the clean interface but would improve initial discoverability.

**Security:**
Observation 2: The wireframe has a basic login screen focusing on user authentication. However, the wireframes lack visible indicators of password strength or complexity requirements. <br>
Suggestion: Implementing password strength indicators and setting a complexity requirement could enhance security. <br>
Tradeoff: Adding these features may increase friction for users during the login process but would ensure a higher level of privacy and data protection.

**Error Tolerance:**
Observation 3: Confirmation dialogs for actions like "SOS Sent" and "Message Sent" indicate an effort to prevent errors but do not appear for all potentially harmful actions (e.g., "Rejecting Invite" & "generating a lottery winner"). <br>
Suggestion: Expand confirmation dialogs to all high-risk actions. <br>
Tradeoff: Adding too many prompts could frustrate users by interrupting workflows, especially for experienced users familiar with the system.

#### Physical
**Fitts’ Law**
Observation 1: Actions like Organize a ROSCA group and Join a ROSCA group as a member are displayed on the permissioning screen with large buttons, making them easy to locate and interact with. <br>
Suggestion: Ensure that the size and spacing of these buttons remain consistent across different device sizes (like mobile and desktop) for accessibility. <br>
Tradeoff: Expanding button sizes may reduce the space available for additional contextual instructions on smaller screens.

Observation 2: Smaller elements like Create reminder or Send SOS are grouped closely in the “Group” screens. While efficient for experienced users, the small size and proximity could pose challenges for users with motor disabilities. <br>
Suggestion: Add padding around smaller buttons and consider providing alternative ways to access these actions <br>
Tradeoff: Increasing the size or spacing of these elements might push other information (like Amount of Money in Pool) further down the screen, potentially requiring more scrolling.

**Mapping**
Observation 1: Navigation menus such as “Home” and “Login” are consistent and logically placed at the top, making it easy for users to understand where they are within the app.<br>
Suggestion: Highlight the current page (e.g., bold the tab or change its color) to reinforce situational context. <br>
Tradeoff: Introducing color changes for active tabs might slightly disrupt the app's overall visual consistency, depending on the chosen design palette.


#### Linguistic
- Our app's wireframe seems to speak a user's language well by using commonplace, nontechnical phrases like "Join a group," "Contribute to pot," etc
- We provide helpful confirmation messages like "Message sent," "SOS sent," and "Invitation sent" to help users evaluate whether they've successfully executed a task
- On a more literal level, our app could speak a user's language even better by having a translation option, since we are targeting more culturally diverse audiences
- Our buttons are labeled quite descriptively with phrases like "Schedule meeting," "Organize/join a group," and "Generate winner," all of which provide users a good information scent for how they can execute certain tasks
- We could provide an even better information scent by adding some central text like "My Groups" or "Group Dashboard" to the page where members/organizers can view all the groups they've joined 

## Project Plan
- Our team will prioritize Permissioning and Scheduling in P4. If there is additional time, we will also attempt to implement Grouping. 
- In P5, we will implement Notifying, Messaging, and if needed Grouping.

#### Division of Tasks (DEADLINE: NOVEMBER 27th)
- [x] **Angel:** Setup Vercel deployment and MongoDB
- [ ] Implement Permissioning
  - [ ] **Ashi:** Implement the back-end
    - Create a data model 
    - Create the data representation 
    - Develop RESTful routes 
  - [ ] **Manasa:** Implement the front-end
    - Implement basic component functionality and reactivity 
    - Front-end data store 
    - Synthesize components into views 
- [ ] Implement Scheduling
  - [ ] **Angel:** Implement the back-end
    - Create a data model 
    - Create the data representation 
    - Develop the RESTful Routes 
  - [ ] **Yonas:** Implement the front-end:
    - Implement basic component functionality and reactivity
    - Front-end data store
    - Synthesize components into views

#### Deadlines
- Back-End: **Due Nov 22, 2024 10:00 PM** 
- Pre-Debug Front-End and Back-End: **Due Nov 25, 2024 8:00 PM** 
- Final Alpha Deployment: **Due Nov 27, 2024 11:59 PM**

#### Backup plan
If we miss a deadline, we can reduce the scope of a concept by getting rid of some of the actions within it (i.e recommending scheduled times). If we encounter a very tight deadline, then we agreed to drop the Messaging concept, as it is simply an additional feature but not core to the functionality of our app. If a pair realizes they can’t implement a concept (or a section of the concept) by the deadline, first, ask for help from the other pair. See if there are any recommendations on simpler implementation, else, go to Dana and ask for any guiding advice. We can also redistribute work, and at worst switch pairs to get some additional hands on the concept. 


