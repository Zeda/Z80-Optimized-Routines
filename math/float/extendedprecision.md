Extended precision (80-bit) routines can be found at [z80float](https://github.com/Zeda/z80float/tree/master/extended). As of this writing, these include:
```
xconst      Locates constants
xabs        Absolute Value
xneg        Negate
xcmp        Compare
xmod1       Discards the integer part (x-int(x))
xrand       rand

xadd        Addition
xsub        Subtraction      (x-y)
xrsub       Reverse Subtract (-x+y)
xamean      Arithmetic Mean

xmul        Multiplication
xfma        Fused Multiply-Add

xdiv        Division
xinv        1/x

xsqrt       Square Root
xgeomean    Geometric Mean
xbg         Borchardt-Gauss mean

xexp        e^x
xpow2       2^x
xpow2_fma   2^x (Uses xfma)
xpow10      10^x
xpow        y^x

xlg         Log2 (Log base 2)
xln         Log (Natural Logarithm)
xlog        LogY (Log base Y)
xlog10      Log10 (Log base 10)

xcos        Cosine
xsin        Sine
xtan        Tangent
xcis        Cosine and Sine
xcosh       Hyperbolic Cosine
xsinh       Hyperbolic Sine
xtanh       Hyperbolic Tangent

xacos       Arccosine
xasin       Arcsine
xatan       Arctangent
xacosh      Hyperbolic Arccosine
xasinh      Hyperbolic Arcsine
xatanh      Hyperbolic Arctangent

xtostr      Extended --> String
xtoTI       Extended --> TI Float
strtox      String --> Extended
TItox       TI Float --> Extended


float.inc   Useful defines and equates
constantsx  Useful constants
data        Data
tables      Tables
```
