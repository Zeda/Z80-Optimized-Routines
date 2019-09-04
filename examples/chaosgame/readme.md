**Chaos Game** (TI-83+/84+ Z80 calculators)

by Zeda Thomas

The Chaos Game is not actually a game, sorry :( Instead, it is a mathematical
tool that is useful for visualizing the output of chaotic systems. The rules are:

* Give a starting point.
* Define N control points.
* Iterate the following forever (or truncate to a finite amount of iterations)
  * Randomly pick one of the N control points.
  * Jump halfway there and plot the pixel.

It is simple enough, but the results can be quite surprising to those not familiar
with the Chaos Game!

# Compile
To compile run something like the following:
```
spasm chaos.z80 chaos.8xp -I ../../
```
