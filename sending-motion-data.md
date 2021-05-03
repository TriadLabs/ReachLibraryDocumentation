---
layout: default
title: Sending Motion Data
nav_order: 2
---

# Sending Motion Data

Sending motion data with the Reach Library is as easy as two quick function calls. The first is a call to the following function:

`ReachLibrary.StartCollectingMotionData(GameObject cameraRig)`

This function will start a coroutine that will automatically save the player’s motion information at predetermined intervals for uploading once the gameplay session is complete. Once the gameplay session is complete and you’d like to stop recording data, a call to the function below will stop sending motion data. 

`ReachLibrary.StopCollectingMotionData()`

We also have a third function to actually upload the data to our database which we recommend calling while displaying a loading screen as it can take between 1-10 seconds depending on the size of the data being uploaded and the internet connection of the player.

`ReachLibrary.SendCollectedData()`

[INSERT PICTURE HERE]
