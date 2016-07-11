---
layout: post
title:  "Sidehelm VR Demo Part 2"
date:   2016-07-10 09:37:36 -0700
categories: demo
---

This week, it was suggested that I try to cast spells with wands, like in
Harry Potter. So I decided to make it happen. A couple things that I learned
how to do:

- Learned how to import assets from the unity store
- Layout the town with convincing forest.
- More about how to manipulate particle systems
- Trigger callbacks for the collision of particles in particle systems
- How to instantiate and destroy particle systems

### Video

Click the thumbnail below to view a video of the demo:

[![Sidehelm VR demo 2](http://img.youtube.com/vi/sqGgfAs7Nn4/0.jpg)](http://www.youtube.com/watch?v=sqGgfAs7Nn4 "Sidehelm VR demo 2")

### The experience

The environment is much more inviting this time around. I was able to build and
design a medieval town square, with a forest nearby. I also was able to make
objects inter-actable, as well as react to the physics.

I can see how game designers can spend a lot of time tweaking things to make
the environment more believable. The suspension of disbelief comes from
attention to detail in most aspects of the world. A tool that one might
be able to sell, is something that helps a designer procedurally generate
natural looking layouts of forests, or natural looking behaviors of objects.

#### Wand movements and spells

In Harry Potter, in order to cast spells, the wizard or witch says the spell
and makes a wand movement at the same time. However, it would be out of scope
to try to use machine learning to do gesture recognition or speech recognition.
Besides, when casting spells, it doesn't add to the game play to have
frustrating ways to cast spells.

Though if this was a real game, I wouldn't make it nearly as easy to cast spells
as pulling the trigger. That tends to cheapen the spell a bit. Maybe if the user
had to charge the spell, by holding the trigger before releasing it, it would
work better.

#### Incendio

When picking spells to cast, an obvious one is a fire spell--like Incendio. I
spent longer than I probably should have trying to decide if fireballs should
be affected by gravity. But as it turns out, gravity makes it more fun, because
then you can shoot them up in the air and have it rain down.

I used a free particle system that implemented fireballs. The fireball particle
system doesn't actually move, but the particle does. So how do you figure out
where the fireball exploded? As it turns out, it's tough to do with the callback.
I had to record the position of the particle as it was traveling. The last known
position of the particle when the callback is triggered is the point where the
center of the explosive force should be.

I also used a smaller radius to find all colliders of objects that needed to
be set on fire, and added fire particle systems that expire for all the collider
objects.

#### Stupefy and Accio

Technically, stupefy should render casters unconscious. But because there are
mostly inanimate objects to interact with, it just pushes them back, like the
[scenes where they're training for Dumbledore's Army][harry-potter].

I used a flash for the spell casting, which again is a particle system. For both
Stuefy and Accio, it uses the same script, except the force is parameterized
in opposite directions. To figure out what the target of the spell is, I just
casted a ray from the wand's direction to any colliders it sees with a rigidbody.

I found that most people don't point the wand directly, and might have to change
the forward direction to angle down a little. But I didn't do it this time.

With stupefy and accio, it's also an impulsive force also, but it's directed
in a forward and back direction.

#### Wingardium Levioso

Levitation is actually pretty tough to get right. I implemented a repulsive force
between the ground and the object, inversely related to distance squared. However,
you need to cap the distance, because if an object is sitting on the ground, the
force is infinite. I decided to cut the scope, so I can move on to the next
demo. But if I were to make more inroads into this demo, I'd make more spells
of this nature.

### Different purposes

People didn't find stupefy nearly as useful as incendio, because they seem to
do nearly the same thing: push things out. So when designing game mechanics, you
need things that have different purposes. So maybe if incendio destroys objects
that you set on fire, then maybe people might want to use stupefy for other
purposes.

There's a lot more to add to the demo, but for one week, it's pretty successful,
and I learned a lot.

The source code is at [https://github.com/iamwilhelm/table_top_demo][table-top-demo-repo].
[Follow me on twitter](https://twitter.com/iamwil). If you have suggestions as
to other demos or exercises to do build next, [tweet at me](https://twitter.com/intent/tweet?text=@iamwil%20)
or send me an email (address in footer).

[table-top-demo-repo]: https://github.com/iamwilhelm/table_top_demo
[harry-potter]: https://www.youtube.com/watch?v=29fvdnzZ0cw&t=4m16s
