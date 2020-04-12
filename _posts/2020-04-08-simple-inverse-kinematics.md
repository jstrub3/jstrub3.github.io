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

![Robotic Arm](/images/robot_arm.jpg)

If foward kinematics determines the endpoint, or end effector, location, then inverse kinematics determines the configuration to reach a given end effector location. This problem is harder to solve for several reasons.  Based on the system complexity and constraints, there could be multiple solutions, or none.  Determining this solution opens up a world of possibilites when it comes to animation.  Characters can reach for items, walk on uneven ground, and otherwise emulate natural behavior.  

## The Algorithm
As implemented by Daniel Schiffman, the algorithm is fairly simple.  Assuming that our target location is Vector P, it goes like this:
1) Set angle of arm so that it 'points' towards P.
2) Move arm location to P.
3) Move arm back 'arm-length' so that it's far end is at P.

![Non-Attached IK](/images/IK_Unity.gif)

That's pretty much it, and Unity has great utility that can help us achieve this.  For starters, the Vector3 system is essential, although we won't be using the LookAt or RotateTowards functions.  Due to Unity's quaternion rotation base, getting the euler angles from a given Transform often doesn't return the expected result.  

There are a couple instances of trigonometric math used, one of which is in step 1).  To determine the angle between the arm and the target, we use:
  angle = arcTangent( target.position.y - arm.transform.position.y, target.position.z - arm.transform.position.z) * 180 / Pi

this gives the X axis rotation of the arm in question (the * 180/Pi part transforms this from radians to degrees), and this can be fed directly into arm.transfrom.Rotate(angle, 0 , 0);

For parts 2) and 3), we use simple vector math to get a 'movement vector' which is calculated as follows:
movementVector = (target.position - arm.transform.position).Normalize();
movementVector = movementVector * -1;       //This turns the vector so it points towards the arm
movementVector = movementVector * armLength;//This magnifies it by the arm size

Now we add this vector to our arm position, essentially lining the arm endpoint with the target position.  Doing this for the next arm in the chain will let us attach many arms to their next component position.

### Attachment Constraint
The above will create an organic looking 'trail' of arms behind the target, but if we want to constrain the arm system to an attachment point, we'll need an additional set of functionality.  The above part works from the target backwards, but the attachment constraint will work from the attachment forwards.  The idea is to set the first link in the arm chain's position to the attachment point, then the next arm's position to the first link's new endpoint position.  Doing this forwards through the whole chain will constrain the entire arm system to a single point, as shown below.

![Non-Attached IK](/images/IK_Unity_attached.gif)

Now this is of course as basic as it gets, there are several more complex IK solutions involving gradient descent or other more complex algorithms.  These are used for a higher degree of constraint or flexibility in solution.  


<a href="https://twitter.com/share?ref_src=twsrc%5Etfw" class="twitter-share-button" data-show-count="false">Tweet</a><script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
