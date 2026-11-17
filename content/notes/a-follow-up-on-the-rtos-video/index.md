+++
title = "A follow-up on the RTOS video"
date = 2026-06-19
+++

A few points came up in the comments on the [RTOS video](https://www.youtube.com/watch?v=i_eU16X67qU), so I wanted to follow up on some of them.

Several comments pointed out that an RTOS is overkill for the example I showed, and I agree. I made the example intentionally small to demonstrate the core idea. That's often the hard part of these videos: to explain something cleanly, you often have to simplify and leave a lot of nuance out.

At the same time, I want to push back a little on the dogmatic view that "an RTOS is almost always a bad idea". Sure, an RTOS has a cost, and you shouldn't reach for it too easily. But strong opinions like that are often shaped by the kind of embedded work someone usually does. I am definitely biased toward using an RTOS, because I mostly work on battery-powered IoT devices these days, where it often fits well. Someone working on very different systems may have the opposite instinct. Both instincts can make sense in the right context, but neither is a universal rule.

The inspiration for the superloop-to-RTOS progression actually came from a pattern I have seen in real projects at work. A system started as a simple superloop, but over time more and more scheduling logic was added by hand, until it has basically turned into a worse version of the thing it was trying to avoid.

I should also clarify that using an RTOS does not mean you stop using interrupts, DMA, timers, or state machines. An RTOS mainly gives you a scheduler and a set of tools for structuring the application, while the code still uses many of the same embedded mechanisms as before.

Several people mentioned approaches that sit somewhere between a simple superloop and a traditional RTOS, including async Rust with Embassy and C++ coroutines. I have to admit I have a bit of a blind spot there, since I tend to think in terms of either "bare-metal loop" or "RTOS". Comparing those approaches could make for an interesting future video.
