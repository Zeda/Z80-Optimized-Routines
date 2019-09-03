# Z80 Optimized (and/or Useful) Routines

This is a repository of routines for the Z80!
As of its inception, it will likely be expanded with the Z80 TI8x series of calculators in mind, but most routines should be general enough for other devices.

Got an idea for how to make this resource better? Please let me know!
Found an optimization? Please share!
Got a useful routine or variation of a routine not yet here? Please add it!
If you want to use a different license from the [default for this repository](LICENSE.md),
then be sure to include it at the start of your file!

If you share a routine that you didn't write, credit the author as best as you can (unless the author doesn't want to be credited).

Thanks!

# How To Use
The way that I am using this repository is by adding it to my Include path with my favorite assembler ([spasm-ng](https://github.com/alberthdev/spasm-ng)). For example:

```
spasm foo.z80 bar.8xp -I ~/asm/z80/Z80-Optimized-Routines
```
Then I can `#include`, say, `mul32.z80` with:
```
#include "math/multiplication/mul32.z80"
```
