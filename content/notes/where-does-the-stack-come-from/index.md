+++
title = "Where does the stack come from?"
date = 2026-08-07
+++

Start with the CPU.

It executes instructions. Those instructions work on data: add two numbers, compare them, move them around.

That data has to sit somewhere the CPU can reach fast, because it's working on it all the time. That's what the registers are for.

But the registers are few because fast memory is expensive. A real program has far more values than they can hold. That's okay, the CPU only works on a few of them at a time. The rest can sit somewhere cheaper, but slower: RAM.

A real program is a long sequence of instructions. The CPU doesn't care. It runs whatever we give it. But that's hard for us to work with, so we break the program into pieces. Functions.

A function is somewhere else in memory. To run it, the CPU must jump to it. And to come back, it has to remember where it was and what it was doing. More data to hold. One jump is fine. But before it jumps back, it may jump to another function, and then another. Once again, the registers are too few to hold all of that. So once again, the RAM.

One block for each jump. Each block has to stay until the CPU jumps back. The next one goes after the last. That forms a pile.

To know where to put the next block, the CPU only has to track where the top is. All that takes is a marker.

The CPU jumps to a function, moves the marker up, and the pile grows. To jump back, it reads the block on top, restores where it was and what it was doing, moves the marker down, and the pile shrinks.

The pile is the *stack*.\
A block is a *stack frame*.\
The marker is the *stack pointer*.

That's the mechanism. It's uglier in practice, but I find it helpful to work out where something comes from first. For one example in practice, watch me hand-decode a real stack in [this video](https://www.youtube.com/watch?v=T59gwneacdk&t=509s).
