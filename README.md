# SplitApp Project 

This is a repository to show the development process of the SplitApp. The initial idea of SplitApp came from my real-life experience with my roommates. I hope SplitApp can bring some convenience to our real life.

If you need to see more details about this project, get the source code, or try to contribute to the SplitApp, please visit https://github.com/SplitAppTeam/Split-App-initial. Thank you~ 

## Table of Contents
1. [Overview](#Overview)
2. [Product Spec](#Product-Spec)
3. [Wireframes](#Wireframes)
4. [Schema](#Schema)
5. [Weekly Project Progress](#weekly-project-progress)

## Overview
### Description
This is an App that helps a group of people to split money more conveniently. It could be the situation when splitting the money with your roommates, or with your friends for a journey. All you need to do is to add the group members' names and the money each member spends that needs to be split, we will generate a bill (or receipt) for each member with the amount they need to pay (or need to receive).

### App Evaluation
- **Category:** FinTech App
- **Mobile:** iOS
- **Story:** This is an App that helps a group of people to split money more conveniently. It could be the situation when splitting the money with your roommates, or with your friends for a journey. All you need to do is to add the group members' names and the money each member spends that needs to be split, we will generate a bill (or receipt) for each member with the amount they need to pay (or need to receive).
- **Market:** Any individual could choose to use this app, and to keep it a safe environment, people just need to enter different group name to track their split bill.
- **Habit:** This app could be used as often or unoften as the user wanted depending on how often he or she is evolved with a group of people who need to split money within the group.
- **Scope:** First we would ask the user to enter an event and the group members for this event and help them split money with each member's financial activities. Then this app could evolve to a personal or group financial management app for them to track their spending.

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* User logs in to see their previous split group bills.
* User logs in and create a new event that requires money splitting with different group members.
* User can invite different users to join the event and split money with them.
* User can enter the activity within a event and how much the activity cost.
* User can assign which group users need to split money for each activity.
* User can assign who pays for the activity.
* ... (more to add)

**Optional Nice-to-have Stories**

* User can chat with all members in the event group.
* User logs in and see the check board for un-paid split events.
* ... (more to add)

### 2. Screen Archetypes

* Log In
* Register - User signs up or logs into their account
* Profile Screen 
   * Allows user to upload a photo and fill in information of their bank account
* Event register - User create a new event
   * Allows user to create a new event and add other users that need to split money together
* Activity add - Each user in the event group can add activities
   * Allows user to add activity, specify who paid for this activity and who need to split this activity in the group
* Settings Screen
   * Lets people change language, and app notification settings.

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Event Register
* Profile
* Settings

Optional:
* Chat - chat in the event group

**Flow Navigation** (Screen to Screen)
* Forced Log-in -> Account creation if no log in is available
* Event Register -> Invite event members
* Profile -> Text field to be modified. 
* Settings -> Toggle settings

## Wireframes
![](https://i.imgur.com/6YJk7KH.jpg)


## Schema 
[This section will be completed in Unit 9]
### Models

#### Event

   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | objectId      | String   | unique id for the user post (default field) |
   | author        | Pointer to User| image author |
   | image         | File     | image that user posts |
   | caption       | String   | image caption by author |
   | event count   | number   | number of events that has been created by the author |
   | Wait to pay   |  Number  | number of events that waiting to get paied |
   | Wait to close | Number   | number of events that are paid by the user but not totally paied back yet|
   | createdAt     | DateTime | date when post is last updated (default field) |
   | updatedAt     | DateTime | date when post is last updated (default field) |

### Networking

#### list of network requests by screen

- Home Feed Screen

  (Create/POST) Create a new event

  (Delete) Delete exisiting event

  (Create/POST) Create a new member in the event

  (Delete) Delete existing member

  (GET) Get all events

- Waiting List Screen
  
  (GET) Get the events that are waiting to pay
  
  (GET) Get the events that are waiting to close

- Create event Screen

  (Create/POST) Create a new event object

  (create/POST) Create a new member object

- Profile Screen

  (Read/GET) Query logged in user object

  (Update/PUT) Update user profile image

#### basic snippets for each Parse network request
- (Read/GET) Query all events where user is author
  ```
  let query = PFQuery(className:"Event")
  query.whereKey("author", equalTo: currentUser)
  query.order(byDescending: "createdAt")
  query.findObjectsInBackground { (events: [PFObject]?, error: Error?) in
     if let error = error { 
        print(error.localizedDescription)
     } else if let events = events {
        print("Successfully retrieved \(events.count) events.")
    // TODO: Do something with events...
     }
  }
  ```

[OPTIONAL: List endpoints using existing Paypal API]

[Paypal In-App iOS Doc](https://developer.paypal.com/sdk/in-app/ios/)

## Weekly Project Progress

## Week 1
#### User Stories:
**Goal**: Initialize the project from scratch.

- [x] User sees app icon in home screen and styled launch screen.
- [x] Set up the sign up and sign in storyboard.
- [x] User can sign up to create a new account.
- [x] User can log in.
- [x] Set up the backend server.
- [x] design app icons 
- [x] Add Parse client to an Xcode project

#### GIF Walkthrough

![SplitApp-week1](https://user-images.githubusercontent.com/75382121/162537395-a80f61f6-a1ed-423e-a8bd-9f9c7e090b88.gif)

## Week 2
#### User Stories:
**Goal**: Keep building the app.

- [x] loginError screen
- [x] create events screen
- [x] cancel button in addAnEvent
- [x] done button in addAnEvent
- [x] add members
- [x] create members table in back4app
- [x] Discuss Paypal API

#### GIF Walkthrough

![SplitApp-week2](https://user-images.githubusercontent.com/75382121/163663752-66601b7b-0cb2-402a-bd73-ba4bfa58c315.gif)

## Week 3
#### User Stories:
**Goal**: Keep adding features to the app.

- [x] user can create event
- [x] user can log in through linked Twitter account
- [x] show existing events on the event feed view controller
- [x] Calculating split amount after entering total payment and the number of members
- [x] AddMember view Controller logics
- [x] user can see details of the event

#### GIF Walkthrough

![SplitApp-week3](https://i.imgur.com/qooOuXc.gif)



