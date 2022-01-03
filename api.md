---
layout: default
title: The Reach API
nav_order: 6
---

# The Reach API
The Reach API allows you to access information from the Reach System using standard REST calls. See the following document for information on calls available to you. We're working on getting additional API's up that you'll need. If you have an API/piece of functionality you require that's not listed on here, let us know and we'll stand one up for you. 

[[/assets/images/api_flow.PNG|API Flow Image]]


## Fetching Data from Reach


## Uploading Data to Reach


## List of Reach API Calls























- - - - - 
- - - - - 
- - - - - 
- - - - - 
- - - - - 
- - - - - 
OLD NOTES

# Retrieving Points from Reach

In order to receive points from the Reach system, you can query our challenge zone 
point API to get a list of points which you can then attempt to prescribe motion to 
during gameplay.  

### Example API Call

[https://staging.reach-vr.com/api/get_challenge_zone_points](https://staging.reach-vr.com/api/get_challenge_zone_points)


# What kind of points will I receive?
If you download the Reach Shoulder Health application from the Oculus Store you can
view the sets of points that we've created that will be coming down with the API. 
Specifically the possible volumes of points that you will recieve from the API are 
named according to the following list:

Triplett:1/14/2021 8:38:34 PM
Triplett:1/14/2021 8:44:51 PM
Triplett:1/14/2021 8:46:11 PM
Triplett:1/14/2021 8:47:25 PM
Triplett:1/14/2021 8:48:41 PM



## Get Session Collision Points

### Inputs

VRMotionCaptureSessionId, hand, collider size. This allows us to get the demonstrated points and prescribed points from a given session and run calculations to determine which points have been "collided" with. 

### Optional Input Parameters

Start/Stop time within session for further granularity. If no times are provided then we go with the entirety of the session

### Outputs

Set of collision points generated as a subset of prescribed points that we've calculated based on given input parameters

### Example API Call

`http://staging.reach-vr.com/api/get_session_collision_points/?session_id=662&session_hand=Left&session_start_time=2020-11-13+17%3A29%3A58&session_end_time=2020-11-13+17%3A30%3A44&segment_sequence_id=0`

Truncated Output: [{"x": -0.2, "y": -0.6, "z": 0.2, "timestamp": ""}, {"x": -0.2, "y": -0.5, "z": 0.1, "timestamp": ""}]

## Get Last Prescribed Assessment Point Set

### Inputs

Oculus Gamertag. This value is necessary in order for the system to know which user’s data to pull from. 

### Optional Input Parameters

None

### Outputs

Most recent set of prescribed points that the given user was given in their last assessment (includes both left and right hand points). Prescribed points are delivered in the following format:


### Example API Call

`http://staging.reach-vr.com/api/get_last_prescribed_assessment_points/?oculus_gamertag=ReachRehab`

Truncated Output: [{"GameId": 1, "Hand": "Right", "CoordinateX": -0.4, "CoordinateY": -0.4, "CoordinateZ": 0.0}, {"GameId": 1, "Hand": "Right", "CoordinateX": -0.4, "CoordinateY": -0.3, "CoordinateZ": -0.1}]





# Future API Calls
The following are a non-exhaustive list of the API calls we will be providing for you to interact with our systems. 

## Receiving Sets of Coordinates
The Reach API provides you the ability to ask for and receive sets of precise gameplay coordinates to recruit motion in specific areas for players.

### Outputs

The function above will return a list of coordinates that the Reach system has determined are appropriate for the player’s next gameplay session. 


## Uploading Demonstrated Data
Submit a seriliazed JSON string to REACH in order for us to process/upload data from gameplay

### Inputs
Oculus Gamertag, Demonstrated Data, Game Identifier

### Outputs
Success Message

