---
layout: default
title: The Reach API
nav_order: 7
---

# The Reach API
The Reach API allows you to access information from the Reach System using standard REST calls. See the following document for information on calls available to you. We're working on getting additional API's up that you'll need. If you have an API/piece of functionality you require that's not listed on here, let us know and we'll stand one up for you. 

![API Flow Diagram](/assets/images/api_flow.PNG)
<span class="caption">API Flow Diagram</span>

## Collecting Motion Data
This method should be called as soon as gameplay begins in order for the Reach System to track motion data. 

StartTrackingMotionData();

Internally this function looks for an instance of the DataCaptureController (or spawns one if it doesn't find one) and has it track motion data every .15 seconds. When the upload function is called the data for that function will come from the DataCaptureController. 


## Fetching Data from Reach
public List<ReachPrescriptionPoint> GetPrescribedPointData(string hand = "Right", int chosenSequence = -1, PrescriptionStyle velocityStyle = PrescriptionStyle.Medium, PrescriptionStyle accuracyStyle = PrescriptionStyle.Medium, int numPoints = 1000)

This method allows games to fetch a list of prescribed points that they can use in their games. The caller of this function must indicate the hand they want to get points for ("Right" or "Left") and the number of points they wish to return. The other parameters are optional unless the user wishes to get a sample set of points which we will define below. 

**Sample Point Sets**
Reach comes with 5 sets of sample points for internal testing of gameplay that can be accessesd with the GetPrescribedPointData method. In order to do so the user must first call the function:

    public void SelectSamplePoints(SamplePointStyle style)
    {
        chosenStyle = style;
    }

SamplePointStyle is an enum with the following values:

    public enum SamplePointStyle
    {
        None,
        FullCapacity,
        FullVolumeMediumElsewhere,
        ChestAndBelow
    }

## Uploading Data to Reach
Uploading data to the ReachSystem should be done anytime a game wants to complete a player's session. To upload data, simply call the following function:

UploadFinishedGameplayData();

This will get the required data from the other Reach objects in the scene (DBManager & DataCaptureController) and send up the prescribed, demonstrated, and collision points associated with the user's gameplay session. 


## Complete List of Reach API Functions

**ReturnToMenu**
This function loads the menu scene and should be called after calling the uploadPoints function to indicate that the gameplay session is complete and that it's time to return the user to the menu.

**GetGridDensity**
This function returns the current grid density (grid spacing) for any game. 

**GetArmLength**
This is a helper function in case any 3rd party experience needs to adjust gameplay because of the individual user's armlength.


## Custom Classes

**ReachGameMetadata**
This class is used to load data from 3rd party games in order for them to be compatible with the Reach Menu. The Reach Menu asks for the following information to be supplied for it to correctly load a 3rd party game. Examples of how this data are used are found on the ReachLibrary object in the Menu scene of the Unity project. 

public class ReachGameMetadata
{
    public Sprite gameSprite;
    public string gameDescription;
    public string gameSceneName;

}


**ReachPrescriptionPoint**
This class is used in the return value for data given to 3rd party games by the ReachLibrary. When requesting a list of points from the Reach System, data is given back as a List<ReachPrescriptionPoint>. The point Vector includes the x,y,z value of the point to prescribe.

public class ReachPrescriptionPoint
{
    public Vector3 point;
    public float accuracy;
    public float velocity;
    public string hand;
}























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

