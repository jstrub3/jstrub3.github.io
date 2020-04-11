---
layout: post
title: Simple Inverse Kinematics in Unity
categories: [blog, code]
tags: [code, animation, unity]
---

(This mini-project was inspired by [Coding Train Inverse Kinematics]({https://thecodingtrain.com/CodingChallenges/064.2-inverse-kinematics.html}) videos)

Every once in a while I like to take a look at part of game development outside of UI.  Some days it's Unity shaders, some days it's Python Flask server framework.  I really like the Coding Train's videos, and I ran across a p5.js version of inverse kinematics.  The idea is 

## Forward Kinematics vs Inverse Kinematics
The simplest way of thinking about kinematics is how we can derive a final destination from a series of vector additions.  Typically supplied via "arm" length and corresponding rotation angles, it's not a terribly difficult problem.  An example of how this is used in games could be robot arm projecting their impact point, allowing quick-fingered players to evade.  Or a construction excavator determing the point of entry of their digging arm.  

![Prim](/images/robot_arm.jpg)

If foward kinematics determines the endpoint, or end effector, location, then inverse kinematics determines the configuration to reach a given end effector location. This problem is harder to solve for several reasons.  Based on the system complexity and constraints, there could be multiple solutions, or none.  Determining this solution opens up a world of possibilites when it comes to animation.  Characters can reach for items, walk on uneven ground, and otherwise emulate natural behavior.  

## The Algorithm
As implemented by Daniel Schiffman, the algorithm is fairly simple.  Assuming that our target location is Vector P, it goes like this:
Set angle of arm so that it 'points' towards P.
Move arm location to P.
Move arm back 'arm-length' so that it's far end is at P.

That's pretty much it, and Unity has great utility that can help us achieve this.  For starters, the Vector3 system is essential, although we won't be using the LookAt or RotateTowards functions.  Due to Unity's quaternion rotation base, getting the euler angles from a given Transform often doesn't return the expected result...


TO BE CONTINUED.



<a href="https://twitter.com/share?ref_src=twsrc%5Etfw" class="twitter-share-button" data-show-count="false">Tweet</a><script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
