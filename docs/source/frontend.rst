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
This component handles comment retrieval, display, and submission for a specific post. It fetches comments from the API based on the provided post ID and authentication token. The comments are rendered as a list of cards, showing the commenter's username and their comment message. Users can enter new comments through an input field, and when the "Comment" button is clicked, the new comment is sent to the API and stored.

Feed
++++++++++++++++
This component handles the retrieval and rendering of a personalized feed of posts, based on the user's followed users. It retrieves the followed users from the API and stores them in an array. It also fetches posts from the API and filters them based on the user's own posts and the followed users' posts. The usernames, post content, and post IDs are stored in separate arrays. The component renders the Post UI component, passing the arrays as props to display the posts.

Post
++++++++++++++++
This component handles rendering a list of posts with expandable comments. It receives arrays of usernames, post content, and post IDs as props, along with a render function to customize the display of each item in the arrays. The component uses material-ui components such as Grid, Container, Card, Button, Typography, and IconButton to structure and style the posts. It also uses the Collapse component to toggle the visibility of comments when the user clicks on the expand icon. The component utilizes the useAuth hook to access the authentication token and user ID. It provides functionality for reacting to posts and posting comments using the api helper functions. The handleExpandClick function expands or collapses the comments section based on the post index. Comments are then displayed using the Comments UI component.

Search
++++++++++++++++
This component provides a search feature for user names. It includes a search input field, a search button, and displays search results. When a user enters a search term and clicks the search button, the component sends a request to the API to retrieve matching user names. The search results are displayed below the search field using the SearchResults UI component.

SearchResults
++++++++++++++++
This component displays the search results for user names. It receives an array of usernames and corresponding Cognito IDs as props. If there are no search results (i.e., the usernames array is empty or undefined), it displays a message indicating that there are no results. Otherwise, it renders a list of cards, with each card representing a search result. Clicking on a card triggers the goToUserPage function, which navigates the user to the user page associated with the selected result by using the Cognito ID.

Theme
+++++++++++++++++
The code defines a custom theme using the Theme interface from the @aws-amplify/ui-react package. The theme contains overrides for different color modes. In this case, the color mode is set to "dark".

Title
++++++++++++++++
This component represents a title bar. If the user is authenticated, it displays buttons and icons for navigating to feed, user profile, and search page, as well as logout.

UserPost
++++++++++++++++
This component represents a form for users to create posts. It includes an input field for entering the post content and a button to submit the post. When the user clicks the "Post" button, an API request is made to save the post on the server. If the post is successful and the content is not empty, it updates the postedToday state.

Routing Components
--------------------

UserRoute
+++++++++++++++++++
This component is used to protect routes that require authentication. It uses the `useAuthenticator`hook from the  @aws-amplify/ui-react library to check the authentication status. If the user is not authenticated, the component renders a <Navigate> component from react-router-dom. This redirects the user to the "/login" route. If the user is authenticated, the component simply renders its children. This allows the protected routes to be displayed.
