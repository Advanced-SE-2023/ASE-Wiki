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
This component represents a page that displays a feed of content, as specified in the Feed UI component. It ensures that the user is authenticated or authorized to view the page by using the UserRoute page component. The page includes a Title page component and a Feed page component.

Login
+++++++++++++++
This component represents a login page that utilizes the AWS Amplify library for authentication. It includes the Authenticator component from @aws-amplify/ui-react to handle the login flow and UI components. Upon successful authentication, the user is redirected to the "/feed" path.

PostPage
+++++++++++++++
This component represents a feed page before posting, which is basically the page where users can post content. It includes the UserPost UI component. The component is wrapped in the UserRoute component to ensure it's only accessible to authenticated users. It also renders a title using the Title UI component.

SearchPage
+++++++++++++++
This component represents a search page where users can perform searches. It includes the Search UI component and the Title UI component. The component is wrapped in the UserRoute component to ensure it's only accessible to authenticated users.

StartPage
++++++++++++++++
This component represents the start page of an application. It renders a title using the Title UI component and includes a welcome message and a link to the login page.

UserPage
++++++++++++++++
This component represents a user's profile page. It retrieves user data, including information about the user, followers, and followed users, and displays it in different tabs. The component includes functionality for following/unfollowing users and navigating to the edit profile page.

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
