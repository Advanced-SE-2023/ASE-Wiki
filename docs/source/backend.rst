Backend
============

The backend was built using Python Django. For developing the API, the Django Rest Framework was used. For storing the data a PostgreSQL Database is set up.

Models
-----------
In Django, database tables are represented by models. The models of ThinkReal. are grouped into the *feed* and *users* sections of the backend. In the following the models are listed with a short explanation and their fields.

Feed
++++++++++++
**Post:** Model representing a user post. It references an instance of CustomUser2 as the post author.

- post_id (primary key)
- content
- created
- custom_user (foreign key)

**Comment:** Model representing a post comment or a post reaction. It references an instance of
Post and one of CustomUser2 (for the commenter).

- comment_id (primary key)
- message
- created
- refd_post (foreign key)
- refd_user (foreign key)

**Notification:** Model holding the following information:
- Who did what, when, on which post, to whom, and does the target know about it?
- Is it time to "thinkreal"?

Admittedly, the Thinkreal notification begs to have its own separate model, but we think
that for this little amount of notification types, the API is simpler by having a single
notification model for now.

- notification_id (primary key)
- created
- action
- is_seen
- refd_notif_recipient (foreign key)
- refd_notif_sender (foreign key)
- refd_post (foreign key)

Users
++++++++++++
**CustomUserManager2:** A custom user manager for retrieving or creating users given a 
JSON Web Token from AWS Cognito.

- cognito_id

**CustomUser2:** Custom user model that inherits from AbstractBaseUser and PermissionsMixin.
The 'second' and final iteration of a custom user integrating with Amazon Amplify and
Amazon Cognito for offloaded user authentication.

This was nearly impossible to do, as it seems very few have done this kind of integration.
Credits to the source: https://sarit-r.medium.com/aws-cognito-and-jwt-token-850dd252750f

- username_validator
- username
- first_name
- last_name
- email
- is_staff
- is_active
- date_joined
- cognito_id

**Follow:** Represents uni-directional friendship relationship between users (n:m).

- follower_uuid (foreign key)
- followed_uuid (foreign key)
- created

API
-----------
The API uses Django Rest Framework. All endpoints use model viewsets
and querysets to minimize code duplication and speed up development.

A ViewSet class is simply a type of class-based View, that does not provide 
any CRUD method handlers. The method handlers for a ViewSet are only bound to 
the corresponding actions at the point of finalizing the view, using the .as_view() 
method. To be used with automatic API routing.

Tradeoff: Using regular views and URL confs is more explicit and gives you 
more control. ViewSets are helpful if you want to get up and running quickly.

On the other hand, CRUD operations in the queryset can still be overridden to
provide e.g. filters on a GET query for a specific model.

The following endpoints are available:

Posts
+++++++++++
| /posts
| /postsearch
| /users/<user_uuid>/posts

/posts returns and modifies the set of all Post objects.
/postsearch returns all Post objects filtered by author username as query parameter (username=<query>).
/users/<user_uuid>/posts returns all post of a user by uuid.

Users
+++++++++++
| /users
| /usersearch

/users returns and modifies the set of all user objects.
/usersearch returns all user objects filtered by username as query parameter (username=<query>).

Following
++++++++++++
| /follow
| /users/<user_uuid>/followers
| /users/<user_uuid>/followed

/follow returns and modifies all Follow relationship objects.
/users/<user_uuid>/followers returns all Follow relationship objects of the followed Users of a User.
/users/<user_uuid>/followed returns all Follow relationship objects of the follower Users of a User.

Comments
++++++++++++
| /comments
| /posts/<post_id>/comments

/comments is a collection of all comments and the endpoint for creation, deletion, 
and modification of comment objects.
/posts/<post_id>/comments returns a list of comments of a given post.

Notifications
++++++++++++
| /notifications
| /users/<user_uuid>/notifications

/notifications is a collection of all notifications and the endpoint for creation, deletion, 
and modification of Notification objects. 
/users/<user_uuid>/notifications gives a user-specific list of notifications to be polled 
by the frontend.

Required arguments
POST:
* action: ['POS', 'COM', 'REA', 'FOL']
* refd_notif_recipient: uuid of recipient user (e.g. post author receiving a comment)
* refd_notif_sender: uuis of sender user (e.g. commenter on post)
* refd_post: only required for action 'POS', post_id
    
PUT:
* notification_id : integer
* is_seen: False by default, to be updated to True when the user sees the notification



Docker images
-----------
Docker images of the backend are available on Dockerhub at https://hub.docker.com/r/ianskoo/thinkreal-backend/tags.


Limitations and further work
-----------
The most important limitation of the backend is the lack of API permission enforcement.
This means (probably) that any Joe could use the API to modify objects at will.