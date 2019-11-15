---
layout: post
title: Refactoring part 1
categories: [blog, code]
tags: [code, refactoring]
---

##What is Refactoring
Refactoring is the boy scout rule of software engineering: "Leave the code better than you found it."  It is taking something that works and transform it into something that works but with 1) less code, 2) less confusion, 3) less complexity, or 4) more extendability.  Honing your brain to look for opportunities to refactor is long-term investing in your own time and the time of your team.

##Less Code
First off, 'less code' doesn't mean to minify scripts or add triple-nested ternary operations.  Forsaking readibility for the sake of reducing lines of code is silly, but I see where this line of thinking comes from.  I wrote the code, I understand it, if I reduce it and I stil understand it, then win-win, right?  Not really, your code will be ready 10x more by other eyes than you. This means bosses, coworkers, contractors 5 years from now, etc.  Readibility should always be priority number 1 when working on a team, even a small team.. even working by yourself!  How many times have you cracked open a dusty old project to think "what was I even doing with this?"

'Less code' means less duplication, redundancy, and repetition.  Moving common constants to Constants.h or a .ini file can work wonders when you want to preserve consistency across sister classes. Creating a base class with common functionality, writing static initializers for lookup maps, etc ensures that when someone else comes along and needs to know BUTTON_ID_25, it's defined clearly in one location (and defined consistently!).

Less code also means that your systems perform as designed, without obvious work-arounds for one-off changes.  An example of this would be a UI element that has a 'redraw' function.  Excellent, when some data changes, the element can be triggered to display that updated data.  But it's never a single piece of data, and data changes multiple times per frame, so how do we deal with this?  Poorly designed systems will call 'redraw' several times over.  Refactoring this might mean adding a 'scheduleRedraw' function, and the actual, expensive 'redraw' happens on a condition in a regular update function.  You might be technically adding more code, but less code is being executed.

##Less Confusion and Less Complexity
Confusion is often the trigger for refactoring in general, which is deeply related to the 'less complexity' goal.  I like to view 'less confusion' refactors as falling into two categories: semantic refactors and function encapsulation refactors.  Semantic refactors include variable, class, and function names.  As code is used and systems changed, things are added to functions or data structures that extend their original purpose.  Ensuring that a data structure named 'TankAmmoData' doesn't including data related to fuel, armor, crew, etc, makes it clear the limitations of it's use.  This leads right into function encapsulation refactors: when a function is no longer limited to it's named purpose, pull the other shit out!  Yes, you are creating more code, but in encapsulating logic, you encapsulate errors.  Stack traces are nicer, and when you encapsulate logic you can categorize data and functions better.  Often when I've pulled out and localized 6-10 additional functions, I find there's enough to make a new class for a singular purpose too.

I would argue that reducing complexity is directly related to the limit-of-functional-scope of your systems functions.  When you know what a function does, and can be assured that it ONLY does that, then debugging becomes a game of deconstruction and reconstruction that's infintely easier than the trial-and-error code changes that can often happen in complex systems.

##More Extendability
Refactoring commonly happens when you are already making changes to a system/class.  A good engineer will think "If I am making X changes now, what about when I need to make Y changes?"  This is how you should approach most changes to existing systems, otherwise you'll find yourself in the exact same situation when a designer requests Y.  Extendable, maintainable code often trumps performant code... and easy-to-read code can always be refactored for performance easier than complex code.

##When to Refactor
###When the Payoff is Clear
You'll eventually hit a system that was put together in such a rush or with so limited scope or by inexperienced engineers that you will think to yourself that this is a teardown job, not just updating the kitchen.  This isn't the best approach; refactoring should be thought of as incremental improvements, each one as their own 'fix'.  Rebuilding entire structures isn't something that can be done for every incremental change, so you'll have to pick your battles and make sure that you aren't dying on the wrong hill.

###When System Coupling is Loose
The more inter-connected and depended your systems are, the harder it will be to refactor anything.  Rippling changes can really be frustrating so ensure the first thing in your mind is this: preserve existing functionality.  Which leads to the last indicator that refactoring can be done...

###When Testing is Robust
The last thing that you want to do when refactoring anything is to break existing function... this defeats the point.  If you can't prove that your changes provide only benefit and no drawback, then this might not be time to tackle refactoring a system.  A testable system is a trustable system, and the last thing you want is for your team to be afraid of changing code.
