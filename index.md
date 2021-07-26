---
layout: home
title: Reach Library Documentation
nav_order: 1
---

# Reach API Documentation
The Reach API allows you to access information from the Reach System using standard REST calls. See the following document for information on calls available to you. We're working on getting additional API's up that you'll need. If you have an API/piece of functionality you require that's not listed on here, let us know and we'll stand one up for you. 

[[/assets/images/api_flow.PNG|API Flow Image]]

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






