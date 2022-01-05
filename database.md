---
layout: default
title: Database Architecture
nav_order: 6
---

1. TOC
{:toc}

# The Reach Database

The Reach system includes 1) the Reach Shoulder Health VR application, 2) a web portal where end-users can view their progress, and 3) 3rd party games and experiences that interface with Reach APIs. Each of these three components may access Reach databases.

Currently, Reach uses a staging database for development/testing and a production database for end-users.

To be granted database access, [contact the Reach development team.](mailto:support@triadlabs.com){:target='_blank'}

In general, changes and additions to the database structure are made and managed via the Django ORM in order to keep everything neat and tidy. If you are developing an application in conjunction with the Reach team and would like to request additions or updates to the database, [contact the Reach DB admin.](mailto:support@triadlabs.com){:target='_blank'}

## Database Architecture

The database architecture for Reach system components can be divided broadly into tables used primarily for/by Django and tables used primarily for/by VR applications.

### Django Tables and Functions

| User Auth, Permissions, & Profiles   | Description         |
|:-------------------------------|:--------------------|
| account_emailaddress           | Django-generated table to track user email addresses |
| account_emailconfirmation      | Django-generated table to track user email addresses confirmations |
| auth_group                     | Django-generated table to manage Django user permissions. Not currently used very much.   |
| auth_group_permissions         | Django-generated table to manage Django user permissions. Not currently used very much.   |
| auth_permission                | Django-generated table to manage Django user permissions. Not currently used very much.   |
| authtoken_token                | Django plugin generated table to manage token authentication. 3rd party developers may request a token, and tokens reside in this table. Tokens currently do not expire.  |
| Client                         | Profile information that is associated with a ReachUser table entry by means of the user_id foreign key. Currently, the most important entry in this table other than the user_id field is OculusLinkId, which represents the value that end-users have entered for their Oculus account usernames.   |
| django_admin_log               | Django-generated table to track admin-related changes  |
| django_content_type            | Django-generated table to parse content types as defined by the Django ORM   |
| django_migrations              | Django-generated table that tracks "migrations," Django's term for changes made to the database via the Django ORM   |
| django_session                 | Django-generated table that tracks Django user sessions   |
| django_site                    | Django-generated table that manages the overall "site" entry/multi-site entries   |


| Additional Tables   | Description         |
|:-------------------------------|:--------------------|
| MarketingSignup                | A table used to integrate Reach web portal sign-ups with 3rd party marketing and user engagement tools.   |


## Reach VR Tables and Functions

| Table Name                     | Description         |
|:-------------------------------|:--------------------|
| MotionCaptureSettings          | Reach uses the settings in this table to define global behaviors for motion tracking and target-generation. |


## Reach VR Table Details

### MotionCaptureSettings

| Field Name                     | Description         |
|:-------------------------------|:--------------------|
| id          | Description goes here. |
| GridDensity          | Description goes here. |
| FireflyLifespan          | Description goes here. |
| MaxFireflies          | Description goes here. |
| NumberOfTimesToPrescribeEachPoint          | Description goes here. |
| CompensationEnabled          | Description goes here. |
| IdleTimeout          | Description goes here. |
| SampleRate        | Description goes here. |
| HitPointThreshold          | Description goes here. |
| FinalRoundTimeInSeconds          | Description goes here. |
| MaxArmLength          | Description goes here. |
| MinArmLength          | Description goes here. |
