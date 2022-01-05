---
layout: default
title: Database Architecture
nav_order: 6
---

# The Reach Database

The Reach system includes 1) the Reach Shoulder Health VR application, 2) a web portal where end-users can view their progress, and 3) 3rd party games and experiences that interface with Reach APIs. Each of these three components may access Reach databases.

Currently, Reach uses a staging database for development/testing and a production database for end-users.

To be granted database access, [contact the Reach development team.](mailto:support@triadlabs.com){:target='_blank'}

## Database Architecture

The database architecture for Reach system components can be divided broadly into tables used for/by Django and tables used for/by VR applications.

### Django Tables and Functions

#### User Authentication, Permissions, and Profiles

| Table Name                     | Description         |
|:-------------------------------|:--------------------|
| account_emailaddress           | Django-generated table to track user email addresses |
| account_emailconfirmation      | Django-generated table to track user email addresses confirmations |
| auth_group                     | Django-generated table to manage Django user permissions. Not currently used very much.   |
| auth_group_permissions         | Django-generated table to manage Django user permissions. Not currently used very much.   |
| auth_permission                | Django-generated table to manage Django user permissions. Not currently used very much.   |
| authtoken_token                | Django plugin generated table to manage token authentication. 3rd party developers may request a token, and tokens reside in this table. Tokens currently do not expire.  |
| Client                         | Profile information that is associated with a ReachUser table entry by means of the user_id foreign key. Currently, the most important entry in this table other than the user_id field is OculusLinkId, which represents the value that end-users have entered for their Oculus account usernames.   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |
| account_emailconfirmation      | good and plenty   |


#### Supporting Django Tables




## Reach VR Tables and Functions

