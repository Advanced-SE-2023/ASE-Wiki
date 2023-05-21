Development Process
====================

Tools
-------------
As a version control system, GitHub is used, because all of the group members are most comfortable with it. To keep switching between tools to a minimum, the development team decided to use GitHub Project for organizing. They set up a Kanban board with all their user stories there. 

Process
--------------
At the beginning of each sprint, a new view in the Kanban board for that specific sprint is created and all user stories planned to finish during the sprint are added. Then each user story is split up into smaller tasks as GitHub issues. During the sprint each developer assigns themselves to the issues that they are interested in tackling and keeps track of their process by keeping the issue in the correct column of the Kanban board.

Each feature (user story) has to be developed using its own branch. Before merging this branch into the development branch, the pull request has to be tested and approved by at least one other developer.

.. image:: /docs/source/Kanban-Board.png
    :alt: Screenshot of Kanban Board on GitHub Projects

Branch Management
--------------------
For this project the Gitflow workflow is used as branch management. Each feature gets its own branch. After being approved, the feature branch is merged into the development branch. For each release the development branch is merged into the main branch. As this is a small project, the release branch is skipped. Bugs can be solved in a Hotfix branch which can be directly merged into main if necessary.

.. image:: /docs/source/clipping-of-git-graph_frontend.png
    :alt: Section of the Git Graph of the Frontend

User Stories
--------------

For each feature or user requirement the development team has specified a user story. The user stories are used to guide development as they include clear requirements and acceptance criteria. In the following the finished as well as the still pending user stories are listed.

Finished
+++++++++++

| US 5: As a user I want to see the posts of users that I follow in my feed in order to keep up with their content without manually looking for it.
| Decision: Must
| Requirement: Users can see the content that users they are following posted, but only after posting themselves
| T-Shirt: M/L
| Acceptance criteria:
- The feed page shows the posts of the users that are followed.
- The posts are shown in order of time posted (most recent on the top).

| US 6: As a user I want to be able to register as a user in order to be able to use the application.
| Decision: Must
| Requirement: Users have a profile page
| The app can only be used when logged in as a registered user
| T-Shirt: M/L
| Acceptance criteria:
- The start page shows a registration option for users who don't have an account yet.
- The registration page asks the user for their name, username, and password.
- Registration creates a new account and stores its information in the database.

| US 7: As a user I want to be able to log in in order to gain access to my personal account.
| Decision: Must
| Requirement: The app can only be used when logged in as a registered user
| T-Shirt: M
| Acceptance criteria:
- The start page shows a login option for users who already have an account.
- The login page asks users for their username and password.
- Logging in shows users their personal feed as well as their personal profile page.
- Trying to log in with incorrect credentials shows an error and doesn't let the user log in.

| US 1: As a user I want to be able to post a text so that my followers can see my post and are able to react to it. 
| Decision: Must
| Requirement: Users can post text content once a day, staying within a character limit
| T-Shirt: L/XL
| Acceptance criteria:
- When a notification is send to the user, the user is able to post a text
- When a user post a text, other users can see the text in their feed
- The user can only write text up to a specified character limit

| US 3: As a user I want to receive a daily notification reminding me to post that day.
| Decision: Must
| Requirement: Users receive daily notifications, prompting them to post a text
| The system notifies each user to post daily at a random time in a specified time range
| T-Shirt: M/L
| Acceptance criteria:
- At the beginning of the day a random time time of day is chosen
- A notification is sent to each user at the previously specified time

| US 12: As a user I want the first thing to see when I open the app be my feed in order to not have to navigate through the application to get to the most important part of it.
| Decision: Should
| Requirement: When a user starts the application, the feed should be available in 3 s
| T-Shirt: S
| Acceptance criteria:
- When opening the application, the first page one is directed to is the feed page.

| US 2: As a user I want to be notified when other users respond to my post so that I see their reaction.
| Decision: Should
| Requirement: Users get notified when others react to their post.
| T-Shirt: M
| Acceptance criteria:
- When a user reacts to another users post, the user gets notified
- The user can see the reactions of other users of a post

| US 4: As a user I want to be able to follow other users in order to connect with them and see their post in my feed.
| Decision: Must
| Requirement: Users can search for other users and see follow them
| T-Shirt: M/L
| Acceptance criteria:
- There is a "follow" button on the profile of each user
- Clicking the "follow" button adds the user to the "follower" list of the other user

| US 8: As a user I want to be able to search for other users to connect with them.
| Decision: Must
| Requirement: Users can search for other users and see follow them
| T-Shirt: M/L
| Acceptance criteria:
- When a username is inserted in the search field the profile of the user is shown.

| US 11: As a user I want to be able to comment under the posts of the users that I follow in order to share what I think about their post.
| Decision: Should
| Requirement: Users can react to the posts of others
| T-Shirt: M
| Acceptance Criteria:
- Users can write comments under the posts of other users.
- Users can see the comments of other users under the post
- The user who's post got commented on will receive a notification

| US 13: As a user I want to be able to choose one of multiple predefined reactions to react to the posts of the users that I follow in order to share what I think about their post.
| Decision: Could
| Requirement: Users can react to the posts of others
| T-Shirt: M
| Acceptance criteria:
- Users can choose from different predefined reactions ("funny", "deep", "sad") to react to a post (think: LinkedIn)
- Users can see the reactions of others on the post
- The users who's post got reacted to will receive a notification

| US 16: As a user, I want to connect with people who have posted themselves so that I can learn about the real lives of the users I follow.
| Decision: Should
| Requirement: Users can see the content that users they are following posted, but only after posting themselves
| T-Shirt: S/M
| Acceptance criteria:
- before a user sees their feed, the system checks if the user has posted in the last 24h

| US 10: As a user I want to be able to change my profile information to keep it up to date.
| Decision: Should
| Requirement: Users can modify their credentials on their profile page
| The system stores each registered user's credentials and content in a database
| T-Shirt: L/XL
| Acceptance criteria:
- personal data like e-mail and username can be changed.

| US 17: As a user, I have a profile page so that my user information is available for others and myself.
| Decision: Must
| Requirement: Users have a profile page
| T-Shirt: M \newline
| Acceptance criteria:
- each user has a profile page
- on the user profile the a users sees the other users today's post

Pending
+++++++++

| US 14: As a user I want to be able to see if another user has posted something within the notification period or after so that I know if the post is spontaneous.
| Decision: Could
| Requirement: Posts of users that have posted too late after receiving the notification are flagged
| T-Shirt: S/M
| Acceptance criteria:
- their is a time limit for each day in which the user should post their post
- if the the time limit is not matched, the post of the user is flagged.

| US 15: As a user I want to be able to choose a specific time period in which I receive the notification so that I am able to post within the time period specified in the notification.
| Decision: Could
| Requirement: Users can specify a time range (minimum of 4 hours), when to get the notification, on their profile page
| T-Shirt: S/M
| Acceptance criteria:
- their is a time limit for each day in which the user should post their post
- As a user I'm able to specify a time range in my profile page, when to receive the notification. The range has a minimum of 4 hours. % klären

| US 18: As a user I want to be able to see how many other users see my post and how they react to it so that I know how many other users receive my posts.
| Decision: Could
| Requirement: Users can see statistics on their posting habits on their profile page
| T-Shirt: L
| Acceptance criteria:
- the user can see statistic on his profile, how many people read their texts

| US 19: As a user I want to be able to edit or delete my posts in order to be able to correct something if I'm not happy with it after posting.
| Decision: Could
| Requirement: Users can edit and delete their posts.
| T-Shirt: S/M
| Acceptance criteria:
- In their profile, users have the option to edit their posts.
- In their profile, users have the option to delete their posts.
- Edited posts are marked as such to the other users.

| US 9: As a user I want to be able to chat with other users in order to keep in touch with them.
| Decision: Could
| Requirement: Users can chat with other users.
| T-Shirt: XL
| Acceptance criteria:
- There is a chat function to write with the other user.
- The chat works in real time

Burndown Chart
-----------------

.. image:: /docs/source/Gantt-Chart.png
    :alt: Gantt Chart of Process on User Stories
