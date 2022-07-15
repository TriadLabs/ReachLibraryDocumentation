---
layout: default
title: API Layer & ReachLibrary Functions
nav_order: 8
---

# The Reach API Layer

Reach is currently undergoing a process of decoupling an API layer from the Reach VR Unity project to make it easier to build new features, modify existing calls, and manage application security. The API layer exists in its own repo and runs in an AWS Elastic Beanstalk Node.js environment.

### Reach Unity API Manager

The Reach Unity project interfaces with the API layer through [an API manager}(https://github.com/TriadLabs/Reach-Shoulder-Health-Unity/blob/master/Assets/APIManager.cs). This manager includes a series of classes that assist with connecting to the middle layer, calling functions, fetching and writing data, and more.


### Collecting Motion Data

[ReachLibrary Function: StartTrackingMotionData](https://github.com/TriadLabs/Reach-Shoulder-Health-Unity/blob/c448728811782c6e4484fd05ea930adceeb8e4d9/Assets/ReachLibrary.cs)

This method should be called as soon as gameplay begins in order for the Reach System to track motion data.

```
StartTrackingMotionData();
```

Internally this function looks for an instance of the DataCaptureController (or spawns one if it doesn't find one) and has it track motion data every .15 seconds. When the upload function is called the data for that function will come from the DataCaptureController. 


### Fetching Data from Reach

[APIManager Function: GetPrescribedPointData](https://github.com/TriadLabs/Reach-Shoulder-Health-Unity/blob/c102e6e26879d98ecd69e1d262cb2cd0dac3e69c/Assets/APIManager.cs)

```
public List<ReachPrescriptionPoint> GetPrescribedPointData(string hand = "Right", int chosenSequence = -1, PrescriptionStyle velocityStyle = PrescriptionStyle.Medium, PrescriptionStyle accuracyStyle = PrescriptionStyle.Medium, int numPoints = 1000)
```

This method allows VR experiences to fetch a list of prescribed points for a given user that may be used to paint targets. The caller of this function must indicate the hand they want to get points for ("Right" or "Left") and the number of points they wish to return. Other parameters are optional unless the user wishes to get a sample set of points which we will define below. 

**Sample Point Sets**

Reach comes with 5 sets of sample points for internal testing of gameplay that can be accessesd with the GetPrescribedPointData method. In order to do so the user must first call the function:

```
    public void SelectSamplePoints(SamplePointStyle style)
    {
        chosenStyle = style;
    }
```
    

SamplePointStyle is an enum with the following values:

```
    public enum SamplePointStyle
    {
        None,
        FullCapacity,
        FullVolumeMediumElsewhere,
        ChestAndBelow
    }
```

## Uploading Data to Reach

[ReachLibrary Function: UploadFinishedGameplayData](https://github.com/TriadLabs/Reach-Shoulder-Health-Unity/blob/c448728811782c6e4484fd05ea930adceeb8e4d9/Assets/ReachLibrary.cs)

Uploading data to the ReachSystem should be done anytime a game wants to complete a player's session. To upload data, simply call the following function:

```
UploadFinishedGameplayData();
```

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

```
public class ReachGameMetadata
{
    public Sprite gameSprite;
    public string gameDescription;
    public string gameSceneName;
}
```


**ReachPrescriptionPoint**

This class is used in the return value for data given to 3rd party games by the ReachLibrary. When requesting a list of points from the Reach System, data is given back as a List<ReachPrescriptionPoint>. The point Vector includes the x,y,z value of the point to prescribe.

```
public class ReachPrescriptionPoint
{
    public Vector3 point;
    public float accuracy;
    public float velocity;
    public string hand;
}
```
