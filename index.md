---
layout: home
title: Reach Documentation
nav_order: 1
---

# The Reach Ecosystem

Reach is on a mission to use virtual reality to help people improve shoulder health. Through a combination of VR experiences and data analysis, we're able to help people improve their mobility, reduce the risk of shoulder pain, and build shoulder strength after surguries, injuries, and other treatments.

Reach is an integrated system of components consisting of:

- A [VR application](https://github.com/TriadLabs/Reach-Shoulder-Health-Unity) developed in Unity (Version 2019.4.33f1) and distributed to end users for use on Meta's Quest device line. The current Quest release candidate is targeted to release on Meta's AppLab distribution channel.
- A [Node-backed API layer](https://github.com/TriadLabs/Reach-Middle-Tier) that is called by the VR application (and, eventually, the web portal) to access and write data to a MySQL server hosted on AWS.
- A [Django + MySQL web application](https://github.com/TriadLabs/ReachPortal2.0) (also hosted on AWS Elastic Beanstalk) where end users can view motion tracking data and progress metrics from the VR application.

## Useful Definitions

Throughout this documentation, you will see references to the terms Volume, Velocity, and Accuracy to describe Reach algorithms and game experiences. In the context of shoulder health, here's a brief primer on each of those terms:

### Volume

In the course of attending to shoulder health, you may encounter the term "range of motion" as a familiar indicator of shoulder mobility and strength. Typically, shoulder health professionals measure and report ranges of motion in terms of degrees of rotation from a given baseline. Reach, on the other hand, measures a user's range of motion in terms of the total volume of 3D space that can be accessed by the user (delimited by that user's arm length). Our 3D-focused algorithms help users understand where they need to focus their training to increase overall shoulder health.

### Velocity

Velocity is an important part of the full picture of shoulder health. If you can access your full volume of motion, but it takes you a very long time to move your shoulder or arm into position, your shoulder is not as healthy as it could be. Reach's approach to measuring velocity is simple-- it is the speed at which a user's controller is moving. 

### Accuracy

Accuracy is another important element of shoulder mobility. For functional and occupational rehab, users who are experiencing decreased shoulder health may be unable to reach into their back pockets, up onto high shelves, or complete other tasks that require complex movement of the shoulder. Accuracy is defined as the degree of closeness of a demonstrated movement of the arm or hand to a specified target in 3D space. You are accurate if your demonstrated motion is close to the true X,Y,Z coordinate value of a target. 






