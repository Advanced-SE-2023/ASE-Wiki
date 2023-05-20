Frontend
=====

The frontend was developed using ReactJS with Typescript. As CSS framework the developers used the MUI library. The frontend communicates to the backend via a RESTful API using Axios.

The start page of the frontend is "App.txs". Here the routing is done and correct page component is rendered, depending on the path.

The frontend is structured into differnt components. The rough structure of the user interface is implemented as a page component. The more fine grained layout of each page is then implemented as a ui component. That way, ui components can be reused by multiple page components (ex. "Title.tsx" is used by every page)

Page Components
------------
The following page components are defined for the application:

ChangePassword
+++++++++++++++

DeleteUser
+++++++++++++++

EditUserPage
+++++++++++++++

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
