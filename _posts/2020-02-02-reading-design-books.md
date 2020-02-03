---
layout: post
title: I'm Learning UX Design, and Here's Why
categories: [blog, code]
tags: [code, ux, design, career]
---

During my morning and afternoon commute, I dedicate this 45 minute period to work-related investment.  Whether it's quick physics programs in Processing.js, or emotional intelligence books, this is at least some time that I can make work for me instead of social-media-zombie-time.  Lately, basic UX design has been my interest and I've found it to be much more helpful that I originally thought.

## Bridging the Discipline Gap
It’s clear that teams work better when everyone is in agreeance as to the plan-of-attack.  Communication between app designers and engineers has the potential to be the most straining part of building software.  You’d initially think that this is due to different end goals (engineers chase performance, designers chase ‘fun’ and positive experiences).  I’ve found this to not be the case, as often the goals are much higher, just to either 1) build something that people will use, or 2) build something fun.  An engineer’s fast, maintainable systems drive this just as much as a designer’s visual framework or game economic strategy.

The real reason that designers and engineers can feel at odds is due to moderate-but-important gaps in knowledge.  Learning to recognize what makes a visual interface good or bad nudges the software design in ways that can really help bring an application together quick.  This post will focus on what software engineers gain by learning about UI/UX design.

## Learning to recognize the most important parts of UX design means that you can make those the most important parts of your engineering.
### Visual consistency
One of the most important aspects of a good UI is that users can quickly, even subconsciously, recognize your UI elements.  Buttons should have the same affordances.  Heading text (used as signposts) should be consistent but distinct from description texts (information for its own sake).  Taking this as an engineer means that I should expect all the styles I build for the first screen/state will be reused across the whole UI.  A list, for example, should be usable across screens, while the list entries should be abstract as to allow certain entries to be highlightable or interactable.  A series of buttons should be built assuming that an “accept” button is very similar to a “cancel” or any other button, but for a single differentiating quality.  
Visual consistency allows users to “not think” and just interact, which leads to less frustration and confusion.  
  
### Many different layout patterns to convey the same information
In addition to consistency, malleability is critical to providing a system that UX designers feel comfortable suggesting changes to (or even switching on the fly for testing purposes).  Knowing that the same information can be presented in a list, grid, tree, fat menu, etc, forces engineers to write UI components that can easily be pushed into different formats.  Learning to separate style from data is important when a design changes late in the project based on some testing or feedback.  Designers benefit from this mindset because they now feel less apprehension about approaching engineers for changes... changes should be properly scoped and prioritized, but welcomed at the same time!

### Priority of human decision making and proper feedback
As described in “Don’t Make Me Think”, people very rarely attempt to make the “best” decision when presented with a series of choices in websites or apps.  They make the quickest “good” decision, with the assumption that they’ll be able to easily fix this if incorrect.  This assumption is crucial, as it forces our software to be as predictable as possible.  We should always strive to provide the best experience for users even if the user makes mistakes.  
As well as human decision making priority, feedback for UI actions also hooks into the lizard-brain that we’re catering to when constructing user-facing software systems.  Sounds, highlights, shadows, movement, scaling, etc are extremely useful tools to be able to implement on everything you build.

### Speaking the designer language
- List inlay vs accordion
- Two panel selector or one-menu drilldown
- Grid of equals != cards != thumbnail gri
Some of these terms might be easy to infer from the design context, but others might not.  And even if visually they can be obvious (I can venture a guess as to how an ‘accordion’ style settings menu might look), the benefits and drawbacks might not be obvious.  Recognizing the terminology that designers use can help to quickly point out issues that would only become visible after considerate construction of the code.  For example, accordions offer collapsable, organized sections to a menu, but space concerns might warrant a tab-panel approach.  If this is part of a mobile app, are the collapse/expand touch areas going to be large enough?  For a console game ensuring proper analog stick navigation could be tricky to make clear to the user in accordions; whereas tabs can be bound to consistent, separate inputs.  List Inlays are very similar to accordions, can they share utility and animation systems for the sake of consistency?

### Shared Vision and Cooperation
After all is said and done, everyone on the team wants to reach the same finish line.  We all want to build things we are proud of, things that bring joy and usefulness to our users.  By taking an active role in the areas of software that 1) engineers are KNOWN to be lacking in and 2) will provide the greatest tangential knowledge we as software developers can bridge the gaps and bring everything together faster and a much more cohesive vision.

<a href="https://twitter.com/share?ref_src=twsrc%5Etfw" class="twitter-share-button" data-show-count="false">Tweet</a><script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
