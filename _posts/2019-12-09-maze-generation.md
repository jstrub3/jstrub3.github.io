---
layout: post
title: Maze Generation Algorithms
categories: [blog, code, games]
tags: [code, refactoring, games, algorithms]
---

## Maze Generation
I implemented several maze generation algorithms in Unity as described on [Wikipedia]({https://en.wikipedia.org/wiki/Maze_generation_algorithm}).  From my experience they tend to fall into two categories: Adding walls to a blank canvas, or removing walls from a completely-full canvas.

## Recursive Backtracker
![Recursive Backtracker](/images/ISxSrYz740kGtPtX(1).gif)
My initial jumping off point as described by Daniel Schiffman in his great [Coding Train tutorial]({https://thecodingtrain.com/CodingChallenges/010.1-maze-dfs-p5.html}) on the subject is the dept-first search recursive backtracking algorithm.  The basic algorithm is:
Randomly walk forward, eliminating walls until you can't walk anymore, then go back to the last walked cell and try to walk again.

## Randomized Kruskal's Algorithm
![Kruskal](/videos/kaJiQXdKKp9qoZNA.gif)
This was interesting in that it involves adding each cell into it's own "set", then joining these sets via a pair of adjacent cells and removing the wall between them.

## Randomized Prim's Algorithm
![Prim](/videos/xo3jgb_haWcO8aYz.gif)
Visually this looked closer to the recursive backtracker, but it differed in that the "tunneling" cell is randomly chosen from a list of visited cells, rather than a single cell going as far as it can.

## Recursive Subdivision
![Recursive Subdivision](/image/EKPTHpIXYAE7D0.jfif)
(This was a little rushed so I don't think it's implemented correctly) The idea is interesting, the maze is divided into segments, separated by a wall, then a random block of the wall is removed.  This can lead to interesting results.


## Lessons Learned
Part of this task was to actually implement the algorithms, but the other part was to do this in the same Unity project, using the same cell, wall, and board assets.  This was a great exercise in how working with a team of various disciplines and values can force you to pivot the structure of your code.  For each algorithm I had to make changes to the way I implemented the cells and walls.  Some required finer directional control, others required addition of walls that wasn't needed before.  By structuring your system in a way that's accepting and welcoming of changes, you can start welcoming design requests instead of dreading them!
