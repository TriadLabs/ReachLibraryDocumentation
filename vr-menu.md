---
layout: default
title: The Reach VR Home Screen
nav_order: 2
---

# Launching the Reach Menu

**Arm Length Calibration/Headset Orientation**

[Unity Scene: Armlength.unity](https://github.com/TriadLabs/Reach-Shoulder-Health-Unity/blob/master/Assets/Scenes/Armlength.unity)

When users first launch Reach, they will first be asked to stand still and face forward with their arms at their side so that Reach can automatically measure their arm length and record this value to the database. Arm length is an important number for Reach, as all downstream VR experiences will inherit this value and scale gameplay accordingly. This calibration step also sets the user's headset orientation for the Oculus experience. All downstream VR experiences launched within the Reach VR Menu should inherit these values.

# The Reach VR Experience Main Menu

[Unity Scene: Menu.unity](https://github.com/TriadLabs/Reach-Shoulder-Health-Unity/blob/master/Assets/Scenes/Menu.unity)

The Reach Main Menu functions as a hub for all of the VR experiences that are available to the user. It is the first screen that the user will see after completing the arm length and headset calibration.

**Left Panel**

This menu allows the user to change settings that affect the Reach experience, such as audio volume, etc. Additionally, there is a collection of settings that appears here only for Reach superusers and testers. These settings appear if a logged in Meta VR user is 1) registered in the production portal database and 2) has the "is_superuser" flag set to 1 in the [ReachUser database table](https://triadlabs.github.io/ReachLibraryDocumentation/database.html).

**Middle Panel**

This menu lists all current Reach VR experiences that are available to the user. Users may select the VR experience they want to play and launch the game from the middle panel. 

**Right Menu**

This menu displays the instructions neccesary to access the Reach Portal. If a user has not signed up for the portal, the right panel will display signup instructions and a "link code" (i.e. their Meta username) which can be used to sign up for the portal.

