---
layout: default
title: Gameplay Parameters
nav_order: 5
---

# Gameplay Parameters

These parameters are used by the Reach Assessment and Firefly Chase Adaptive modes to determine the relevant aspects of their gameplay. Specifically, the Assessment modes use the values given in the MotionCaptureSettings table while the Adaptive mode uses  

**Grid Density**

This refers to the space between generated points in a given volume. Reducing this value decreases the space between points and results in more potential points being generated while increasing it does the opposite. Default value is .1 which gives us a good balance between spacing and making sure that gameplay doesn't take too long. Lower densities are better for getting a more accurate picture of someone's capacity but take longer to complete. For larger volumes it's recommended to increase this to a value such as .14. 

**Firefly Lifespan**

This refers to the amount of time a firefly will stay spawned in during the game before fading away and being counted as a missed target. Default value is 12 seconds.

**Max Fireflies**

Max number of fireflies to spawn at any one time. This value is respected for the assessment but in Firefly Chase the volume defintion that drives gameplay can override this base value. Default value is 8

**Number of times to prescribe each point**

This refers to the number of chances we give someone in the assessment to hit a point. We leave this value intentionally high in order to provide the user with a good number of chances. This is something we're considering removing and moving back to an internal parameter. Default value is 10.

**Compensation Enabled (Deprecated)**

Leave this set to 0. This is a parameter that allowed us to control whether the compensation module we developed would be used by the game. We've since removed the module and no longer include it in our SDK.

**Idle Timeout**

This sets the timeout during normal gameplay. A warning will play after half the idle timeout time has elapsed. Default value is 12 seconds.

**Sample Rate**

This allows you to change the rate at which data is collected. A value of 1 means that one data point is collected every second. Default value is .1 which means 10 points of data are collected per second.

**HitPointThreshold**

This value allows you to change the size of the collider around the hand to determine what counts as a "collision point" or hit point.

**FinalRoundTimeInSeconds**

This parameter allows you to set the timeout for the final round. Default value is 12 seconds.

**MaxArmLength**

This is the upper bound to what the game considers an acceptable arm length. The purpose of this parameter is to ensure that an erroneous reading does not completely break the system (if we somehow got a negative or close to 0 reading). The default value is 1.1 (during testing our armlengths hover between .6-.75 depending on who is testing).

**MinArmLength**

This is the lower bound to what the game considers an acceptable arm length. The purpose of this parameter is to ensure that an erroneous reading does not completely break the system (if we somehow got a negative or close to 0 reading). The default value is .3
