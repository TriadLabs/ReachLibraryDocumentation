---
layout: default
title: Adaptive Experiences
nav_order: 4
---

# Reach Adaptive Experiences

Reach's Adaptive Experiences are designed to accept a variety of inputs from the end user, which are then analyzed by the Reach API layer and used to output the variables for a VR game experience that is optimized for that user's shoulder health needs at that moment in time.

Currently, Reach has a roster of two adaptive experiences.

### Firefly Chase

[Unity Scene: SubzoneAssessment.unity](https://github.com/TriadLabs/Reach-Shoulder-Health-Unity/blob/master/Assets/Scenes/SubzoneAssessment.unity)

<p style="color:red;">NOTE: The current build of Firefly Chase is inoperative. The following notes represent the design specifications for a future development cycle.</p>

The gameplay of Firefly Chase is designed to encourage users to hit points that are deemed challenging (just on the edge of possible) by the Reach API layer.

Generally a series of 100 points will be prescribed for the user to hit (based on the user's last volume assessment values), with 80 being points the Reach system is confident they can hit, and 20 being points that the system is unsure if they will achieve. The experience ends after the user has played for 3 minutes.

### Space Gunner

[Unity Scene: SpaceGunner.unity](https://github.com/TriadLabs/Reach-Shoulder-Health-Unity/blob/master/Assets/SpaceGunner/Scenes/SpaceGunner.unity)

Space Gunner is also designed to encourage users to hit points that are deemed challenging by the Reach middle tier. Currently, Space Gunner fetches a set of placeholder points from the API layer and uses the targets to generate a 3D battle map scene in which users must fire weapons at targets to destroy enemy ships. Future development cycles will fetch a set of "smart" points from the API layer instead of the current placeholder set.
