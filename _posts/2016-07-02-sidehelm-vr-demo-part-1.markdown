---
layout: post
title:  "Sidehelm VR Demo Part 1"
date:   2016-07-02 09:37:36 -0700
categories: demo
---

Getting started with Unity was fairly easy, as there's lots of video tutorials,
both on youtube, and unity's site itself. The short demo was a bit involved.

- Build hands to track the controllers
- Use the hands to pick up the objects, and the objects tracked the hand correctly.
- Incorporate a time delay into the objects tracking the hand to give a sense of weight.
- Use Unity3D physics to make sure the balls and cubes don't go through the floor, and the ball bounces.
- Use trigger colliders to keep track of a score and shoot confetti.
- Used a particle system to shoot confetti.

### Video

Click the thumbnail below to view a video of the demo:

[![Table top VR demo 1](http://img.youtube.com/vi/GQAFp4_P6bM/0.jpg)](http://www.youtube.com/watch?v=GQAFp4_P6bM "Table Top VR demo 1")

### The experience

The toughest part of the entire exercise was handling the hand interaction. It's
actually somewhat involved, to take into account weird edge cases. There were
unexpected bugs, like the object keeps rotating while it's in my hand, or once
I picked it up, I can keep interacting with it at a distance. One time, I had
forgotten I zeroed out the velocity so the object doesn't keep moving in my hand,
but when I went to throw it, the object would just drop to the ground.

Everything else was pretty straight-forward, however. I've written toy game
engines before, and it's really nice that Unity provides the entity-component
system up front. I was able to build a hoop, with a trigger collider that updated
the scoreboard as well as shoot confetti when you scored.

One trick with the hoop score counter, is that you have to be sure the ball is
entering the hoop from above, instead of below, for it to count as a point. To
check for that, when an object entered and exited the hoop's trigger collider box, I
checked to see that the velocity in the y direction was negative. And if that was
true both times, then it counts as a point.

Particle systems are quite hard to get right. Though the module system makes it
easy to configure and play around with in real time, it actually took a while
for me to get it to look right. That's probably why the asset store has particle
systems for people to use, instead of configuring it all on your own.

The source code is at [https://github.com/iamwilhelm/table_top_demo][table-top-demo-repo].
[Follow me on twitter](https://twitter.com/iamwil). If you have suggestions as
to other demos or exercises to do build next, [tweet at me](https://twitter.com/intent/tweet?text=@iamwil%20)
or send me an email (address in footer).

[table-top-demo-repo]: https://github.com/iamwilhelm/table_top_demo
