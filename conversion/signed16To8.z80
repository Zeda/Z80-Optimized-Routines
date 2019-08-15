;This amazing routine is by Runer112
;"Here's a very optimized way to convert a 16-bit signed number into an 8-bit
;signed number in a with overflow handling (if hl<-128, a=-128; if hl>127, a=127).
;Two added bonus to being super small and super fast are that it destroys nothing
;and that you could easily modify it to make the input a 16-bit register other
;than hl."

Signed16To8:
 ld a,l
 add a,a
 sbc a,a
 sub h
 ld a,l
 ret z
 ld a,h
 add a,a
 sbc a,a
 xor %01111111
 ret
