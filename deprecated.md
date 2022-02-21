---
layout: default
title: Deprecated Features
nav_order: 12
---

# Deprecated Features

This page will detail the features that were deprecated from the Reach System in the (INSERT GIT ID HERE) push on (DATE). Should any of these features need to be revived, their locations and relevant scenes and purposes are described below.

**Compensation**

We built a variety of different compensation prototypes to solve the problem where users kept moving their heads or feet during experiences. This caused our data collection to suffer in quality or else give the user the impression that they had achieved a very good range of motion score only to be dissapointed when they saw their data later (which we adjusted automatically for compensation). The prototype that's in the Reach Shoulder Health application is essentially an invisible bubble that surrounds the player. Shoudl their head deviate from the range of the bubble, we then show them their deviation + a popup asking them to move their head back to the playspace. 

**Climbing Experience**

We wanted to test how to recruit a more game like up/down motion with the hands. To that end we built 2 climbing experiences. One, Space Climb, is a separate experience (and on a previous version of Unity). The other can be found in Scenes>Testing>Noncore. There we experimented with having the player move their hand along a rope attached to a pulley.

**Subzone Pathing**

In this experience we experimented with the idea of having the user follow a pre-determined path that was revealed to them over time. Imagine a line of points where when the first point in the sequence is hit, the next immediately appears. We also had a feature that reset the path in case the user's hand deviated from the path that we had drawn for them. 

**Prescription Algorithms**

We built a number of different point generation algorithms including a grid based one, a convex hull generator/consumer, and more which are detailed on the Targets and Collisions page of the docs.
