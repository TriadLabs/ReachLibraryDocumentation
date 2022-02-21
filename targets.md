---
layout: default
title: Targets and Collisions
nav_order: 7
---

# Painting Targets and Calculating Collisions

Reach uses a set of algorthims to determine how to paint targets for different game modes as well as calculate collisions. We make a distinction between targets that are achieved from a gameplay perspective and those that are calculated to be collisions by the Reach system. This is because gameplay usually doesn't account for head movement/compensation while the Reach system. 

**Calculating Prescribed Targets**

Our original approach to spawning targets (since deprecated) was to construct a 3D grid of points equidistant from each other in a cube shape. We had parameters that adjusted the distance between each point as well as the limits on the x,y, and z axis. From there we inserted rules to trim the shape to match what we thought was a good range of motion for a human arm span. This worked reasonably well but constructing ever more intricate rules forced us to rethink how we wanted to go about things. 

Next, we built a system that allowed the user to define the exterior points of a convex hull that we stored in the database. By accessing the DataRecorder scene you can create and save a VolumeSegmentSequence which could then be read by our system to create the convex hull and sample points within it (equidistant from each other). The consumer of these recorded data points always adjusted given points by first dividing by the recorders armlength before multiplying each point by the current user's armlength.

Our current approach relies on receiving a set of coordinates from the database that are then displayed to the user in random order. The Reach System relies on the Assessment to establish the ground truth on which points are considered completely within a user's reach and which points are outside their current effective reach. Our challenge modes intermix a combination (80% within, 20% out of reach) of these points. 

Currently performance in challenge modes does not affect future challenge mode point generation. Only assessments can modify the points that are generated for challenge zone modes. 


**Calculating Collision Points**

The Reach collision algorithm can be found in DBManager.cs under the function (RecalculateDensity). 

In order to calculate collisions we iterate over every "demonstrated" point of motion that we saw (this refers to the motion coordinates we captured from the hand controllers adjusted for head compensation) and then compare that points Vector3.Distance to each prescribed point. If it's below our threshold for a collision point (this threshold defaults to .14 and is analgous to a collider size in Unity) then we count that prescribed point as hit. This is an N squared operation (since we iterate over both demonstrated and prescribed points) which makes it time consuming so there's room for improvement here. 

Collision calculations are set in motion by a call to UploadData in DBManager which ours/3rd party experiences call once a gameplay session is complete. These collision points are then used to determine which points to prescribe in later experiences (as collided points are considered completely within a user's reach).

