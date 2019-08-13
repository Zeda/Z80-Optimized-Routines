;Created by calc84maniac
;NOTE from Zeda: C should <=128, the original forgot to mention this.

DEHL_Div_C:
;Inputs: dehl=32-bit dividend, c<=128 is the divisor (Or is it the other way around?)
;Outputs: dehl=32-bit quotient, a=remainder, c=unchanged, b=0
;min: 1936cc
;max: 2032cc
;avg: 1984cc
;Size: 17 bytes
div32bit:
 ld b,32
 xor a
divloop:
 add hl,hl
 rl e
 rl d
 rla
 cp c
 jr c,divlbl
 inc l
 sub c
divlbl:
 djnz divloop
 ret
