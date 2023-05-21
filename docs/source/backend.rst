Backend
============

The backend was built using Python Django. For developing the API, the Django Rest Framework was used. For storing the data a PostgreSQL Database is set up.

Models
-----------
In Django, database tables are represented by models. The models of ThinkReal. are grouped into the *feed* and *users* sections of the backend. In the following the models are listed with a short explanation and their fields.

Feed
++++++++++++
**Post:** Represents a post

- post_id (primary key)
- content
- created
- custom_user (foreign key)

**Comment:** Represents a comment

- comment_id (primary key)
- message
- created
- refd_post (foreign key)
- refd_user (foreign key)

**Notification:** Holds information on different notifications

- notification_id (primary key)
- created
- action
- is_seen
- refd_notif_recipient (foreign key)
- refd_notif_sender (foreign key)
- refd_post (foreign key)

Users
++++++++++++
**CustomUserManager2:** A custom user manager for creating and retrieving users from AWS Cognito

- cognito_id

**CustomUser2:** Custom user model that inherits from AbstractBaseUser and PermissionsMixin.

- username_validator
- username
- first_name
- last_name
- email
- is_staff
- is_active
- date_joined
- cognito_id

**Follow:** Represents uni-directional friendship relationship between users (n:m)

- follower_uuid (foreign key)
- followed_uuid (foreign key)
- created

API
-----------
The following endpoints are available:

Posts
+++++++++++
/posts
/postsearch
/users/<user_uuid>/posts

Users
+++++++++++
/users
/usersearch

Following
++++++++++++
/follow
/users/<user_uuid>/followers
/users/<user_uuid>/followed

Comments
++++++++++++
/comments
/posts/<post_id>/comments
