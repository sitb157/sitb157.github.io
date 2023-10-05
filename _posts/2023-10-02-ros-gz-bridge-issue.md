---
layout: post
title:  a post with ros_gz_bridge issue log
date: 2023-10-02 21:01:00
description: this is log to archive issue
tags: issue
categories: sample-posts
thumbnail: assets/img/IMG_3356.png
---  
### Issue Encountered During Gazebo Garden Installation and Demo Test  
#### ros_gz_bridge error  
During the installation and demo test of Gazebo Garden, I encountered an issue with the ros_gz_bridge.  
Specifically, when using the parameter_bridge, the data was not being transferred to ROS 2 topics as expected.  
I followed the example provided [here]((https://index.ros.org/p/ros_gz_bridge/), but the issue persisted. In my search for a solution,  
I came across a similar issue.  Despite attempting the suggested solutions in the [issue](https://github.com/gazebosim/ros_gz/issues/365)  
however, the problem remained unresolved.  
![image](https://github.com/sitb157/sitb157.github.io/assets/108820413/c42cfc6f-3917-47e1-b666-27478a023f12)<br/>  
I eventually managed to resolve the issue by specifying the GZ_VERSION more explicitly in my Dockerfile when I was creating it.  
![image](https://github.com/sitb157/sitb157.github.io/assets/108820413/4514ac9a-a82d-4b65-915c-d47f294b369e)<br/>  
This change seemed to do the trick, and I was able to receive sensor data and other topics using ros2 topic echo after modifying  
