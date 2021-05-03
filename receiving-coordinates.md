---
layout: default
title: Receiving Coordinates
nav_order: 3
---

# Receiving Sets of Coordinates
The Reach Library also provides you the ability to ask for and receive sets of precise gameplay coordinates to recruit motion in specific areas for players. There are a number of different parameters that you can use to get specific types of coordinates which are detailed in the appendix.

`ReachLibrary.GetCoordinates(int numberOfCoordinates)`

The function above will return a list of coordinates that the Reach system has determined are appropriate for the player’s next gameplay session. As long as you’ve enabled the collection of motion data, our system will automatically recognize when the player reaches any of the “prescribed” points that were sent down by the system. 

The following function allows you to specify gameplay constraints that the Reach system will use in determining the coordinate limits aga

`ReachLibrary.GetCoordinates(CoordinateConstraints axisConstraints, int numberOfCoodinates)`

We also provide a number of different ways to specify constraints on coordinates based on gameplay, timing, or other factors. If your experience requires the need for new parameters which have not been covered please contact us and we’ll work with you to ensure that an API is created for your needs.
