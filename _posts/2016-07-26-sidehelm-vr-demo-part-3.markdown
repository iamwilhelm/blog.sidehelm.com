---
layout: post
title:  "Sidehelm VR Demo Part 3"
date:   2016-07-26 10:00:00 -0700
categories: demo
---

![Multitude Screenshot](/assets/images/multitude_screenshot.png)

One guiding light I have about VR is that it immerses you completely in a world
of your own choosing. You could choose another time, or another place, but
the most fascinating option is to choose a place where there is magic.

It can be magic in the traditional sense, like
[Harry Potter in Week 2 Demo][demo-2]. But it can also be magical where you
bend just a single rule of physics. What if you could record your movements
and play it back for yourself? Taking it one step further, what if you can
not only watch the playback, but the recording is there with you in real
life, and it does work with you?

In VR, surprisingly, you don't need very much to get a sense of presence
of another person. All you need is low-latency tracking of the head and
hands, and directional audio.

Many of us have fantasized about having another version of us to help us
with all the things that we want to do. This week, I made something that
lets us partake in that type of magic with inspiration from the late Harold
Ramis's movies, [Groundhog Day][groundhog-day] and the flash game
[Cursor * 10][cursor*10].

![Multitude Title](/assets/images/multitude_title.png)

The working title is "Multitude" right now (subject to change). The story is
that a King dropped his coins on the way back to his castle, and it's up to
you to pick up after him. I think there's a larger underpinning and story
to such a concept. But for now, it's in keeping with the assets I used.

I learned a couple things these two weeks. Some technical, and some in design.
This piece of code had more moving parts than previous demos.

I learned how to:

- record motion and play it back.
- teleport a player to different places.
- make a functioning button that triggers state in other objects
- make objects collectable

### Game design

But more interesting, I also learned some things about game design. I had
certain aspects of the world I needed to teach the user, like how teleportation
works.

How do you teach teleportation? For one, the player has to recognize the
object as a teleportation device. I modeled it after the star trek teleporters
But also, I added a particle system that indicates whether the teleporter is
on or not. Details are important, only in so far as being able to communicate
that this is a spot that you need to step into.

But that's not enough. You need particle systems to both indicate that a
teleport has occurred on the teleportation pad, but also on the person that
teleported. Otherwise, it will seem as if they were jerked to a different
spot suddenly. A user need to 'materialize'.

In addition, teleportation needs to teach where the player has teleported
to, as well as where she has teleported from. To achieve this, I purposely
placed all initial levels in a line, so they can see recognizable and
unique landmarks up ahead. That way, when they teleported, they can reorient
themselves with the landmarks.

I also purposely placed the teleportation in the corner of the room, where the
player would be looking at the previous level. That way, they can see the
previous level, as well as the glitter that indicates where they teleported
from.

How do you teach cloning? That was a much tougher task. I was hoping that
people would remember what tasks they were doing, and be able to see the
clones repeating them. However, in preliminary tests, players didn't recognize
their own actions. They simply thought there was suddenly other characters
around doing other things.

I tried to mitigate this by putting numbers above the clones' heads. But I
may need to add a mirror on the title level, or there needs to be a pause
between clone plays that says "Clone No. X, Ready?" I may do that when
I swing back to it.

### Screencast

Click the thumbnail below to view a screencast of the demo:

[![Sidehelm VR demo 3](https://img.youtube.com/vi/asdf/0.jpg)](https://www.youtube.com/watch?v=asdf "Sidehelm VR demo 3")

### Source

The source code is at [https://github.com/iamwilhelm/table_top_demo][table-top-demo-repo].
[Follow me on twitter](https://twitter.com/iamwil). If you have suggestions as
to other demos or exercises to do build next, [tweet at me](https://twitter.com/intent/tweet?text=@iamwil%20)
or send me an email (address in footer).

[groundhog-day]: http://www.rogerebert.com/reviews/great-movie-groundhog-day-1993
[cursor*10]: http://jayisgames.com/games/cursor-10/
[demo-2]: https://iamwilhelm.github.io/blog.sidehelm.com/demo/2016/07/10/sidehelm-vr-demo-part-2.html
