---
layout: default
title: API Reference
nav_order: 5
---

# API Reference

## Get Session Collision Points

### Inputs

VRMotionCaptureSessionId, hand, collider size. This allows us to get the demonstrated points and prescribed points from a given session and run calculations to determine which points have been "collided" with. 

### Optional Input Parameters

Start/Stop time within session for further granularity. If no times are provided then we go with the entirety of the session

### Outputs

Set of collision points generated as a subset of prescribed points that we've calculated based on given input parameters

### Example API Call

`http://127.0.0.1:8000/api/get_session_collision_points/?session_id=662&session_hand=Left&session_start_time=2020-11-13+17%3A29%3A58&session_end_time=2020-11-13+17%3A30%3A44&segment_sequence_id=0`

## Get Last Prescribed Assessment Point Set

### Inputs

Oculus Gamertag. This value is necessary in order for the system to know which user’s data to pull from. 

### Optional Input Parameters

None

### Outputs

Most recent set of prescribed points that the given user was given in their last assessment (includes both left and right hand points).

### Example API Call

`http://127.0.0.1:8000/api/get_last_prescribed_assessment_points/?oculus_gamertag=Roosh`



