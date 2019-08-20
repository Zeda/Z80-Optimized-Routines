Single precision routines can be found at [z80float](https://github.com/Zeda/z80float/tree/master/single). As of this writing, these include:
```
absSingle       Absolute Value
cmpSingle       Compare two floats
negSingle       Negate
intfrac         Gets the integer part of a float
mod1Single      Gets the fractional part of a number (x-int(x))
randSingle      rand

addSingle       Addition
rsubSingle      reverse subtract (y-x instead of x-y)
subSingle       Subtraction
ameanSingle     Arithmetic mean

mulSingle             Multiplication
mul10Single           Multiplication by 10
mulSingle_p375        Multiplication by .375
mulSingle_p34375      Multiplication by .34375
mulSingle_p041015625  Multiplication by .041015625

divSingle           Division
invSingle           1/x
divSingle_special   Special-purpose divisions

sqrtSingle      Square Root
geomeanSingle   Geometric Mean


bg2iSingle      Computes the Borchardt-Gauss mean to limited precision
bgiSingle       Computes the Borchardt-Gauss mean

expSingle       Exponential Function
pow2Single      2^x
pow10Single     10^x
powSingle       x^y

lnSingle        Log  (Natural logarithm)
lgSingle        Log2 (Log base 2)
log10Single     Log10 (Log base 10)
logSingle       LogY (Log base Y)

single2char     Converts a float to an unsigned 8-bit integer
singleTo_int16  Converts a single to a signed 16-bit integer
single2str      Single --> Str
str2single      String --> Single
single2TI       Single --> TI Float
ti2single       TI Float --> Single


cosSingle       Cosine
sinSingle       Sine
tanSingle       Tangent
cisSingle       Cosine and Sine  (faster than individually computing both)
coshSingle      Hyperbolic Cosine
sinhSingle      Hyperbolic Sine
tanhSingle      Hyperbolic Tangent

acosSingle      Arccosine
asinSingle      Arcsine
atanSingle      Arctangent
acoshSingle     Hyperbolic Arccosine
asinhSingle     Hyperbolic Arcsine
atanhSingle     Hyperbolic Arctangent

single.inc      Useful equates
lut             Look-up Tables
constants       Contains useful constants
data            Data

```
