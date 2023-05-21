Frontend
=====

The frontend is developed using ReactJS with Typescript. As CSS framework the developers are using the MUI library. The frontend communicates to the backend via a RESTful API using Axios.

The start page of the frontend is "App.txs". Here the main App component is defined, which wraps the app in the Authenticoator and ThemeProvider. Alsoe the routing is done here.

The frontend is structured into differnt components. The rough structure of the user interface is implemented as a page component. The more fine grained layout of each page is then implemented as a ui component. That way, ui components can be reused by multiple page components (ex. "Title.tsx" is used by every page)

Page Components
------------

ChangePassword
+++++++++++++++
This component provides a form for changing the user's password. It utilizes various UI components from the "@aws-amplify/ui-react" library and integrates with the user authentication system using the `useAuth` hook. Upon successful password change, it displays an alert and navigates to the user's edit page.

DeleteUser
+++++++++++++++
This component provides functionality for deleting the user's account. It utilizes various UI components from the "@aws-amplify/ui-react" library and integrates with the user authentication system using the `useAuth` hook. Upon successful deletion, it displays an alert, navigates to the home page, and triggers the sign out process.

EditUserPage
+++++++++++++++
This component retrieves the user's information from the backend API and displays a form to edit the first name, last name, and email fields. It integrates with the user authentication system using the `useAuth` hook. The edited information is then saved to both the backend and the Cognito user pool. The component also provides options to change the password and delete the account which will render the according component.

FeedPage
+++++++++++++++

Login
+++++++++++++++

PostPage
+++++++++++++++

SearchPage
+++++++++++++++

StartPage
++++++++++++++++

UserPage
++++++++++++++++

UI Components
------------

Comments
++++++++++++++++

Feed
++++++++++++++++

Post
++++++++++++++++

Search
++++++++++++++++

SearchResults
++++++++++++++++

Theme
+++++++++++++++++

Title
++++++++++++++++

UserPost
++++++++++++++++

Routing Components
--------------------

UserRoute
+++++++++++++++++++
