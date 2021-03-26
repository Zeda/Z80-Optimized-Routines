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

# Other Resources
[https://www.omnimaga.org/asm-language/asm-optimized-routines/](Omnimaga's "ASM Optimized Routines")
[https://www.cemetech.net/forum/viewtopic.php?t=1449](Cemetech's Useful Routines)
[https://www.cemetech.net/projects/uti/viewtopic.php?t=1279](United TI's Useful Routines)
[http://z80-heaven.wikidot.com/](Z80 Heaven) (has optmization tricks and useful routines)
[https://wikiti.brandonw.net/index.php?title=Z80_Optimization](wikiti Generic optimizations)
[https://gist.github.com/raxoft/c074743ea3f926db0037](32-bit xorshift)
[https://gist.github.com/raxoft/2275716fea577b48f7f0](cmwc (Complementary-Multiply-With-Carry) RNG, very cool)
