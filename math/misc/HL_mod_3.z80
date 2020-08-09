#ifndef included_HL_mod_3
#define included_HL_mod_3

HL_mod_3:
;destroys HL, returns HL mod 3 in A
;112+{0,2} + {0,8} + {0,1}
;min: 112
;max: 123
;avg: 117.5
  ld a,h
  add a,l
  adc a,0

#ifndef included_A_mod_3
#define included_A_mod_3
A_mod_3:
;destroys HL, returns A mod 3 in A
;97+{0,2} + {0,8} + {0,1}
;min: 97
;max: 108
;avg: 102.5
#endif
  ld l,a
  add a,a
  add a,a
  add a,a
  add a,a
  add a,l
  jr nc,$+4
  add a,16
  ld l,a
  add a,a
  add a,a
  ld h,%11000000
  and h
  add a,l
  jr nc,$+3
  sub h
  and h
  rlca
  rlca
  ret po
  xor a
  ret
#endif




;Here is the more commented version:

; HL_mod_3:
; ;destroys HL, returns HL mod 3 in A
; ;112+{0,2} + {0,8} + {0,1}
; ;min: 112
; ;max: 123
; ;avg: 117.5
;
; ; HL mod 3 == (H*256+L) mod 3 == (H*1+L) mod 3 == (H+L) mod 3
; ;So add the upper and lower byte
;   ld a,h
;   add a,l
;
; ;If adding caused an overflow, well add (256 mod 3) == 1 to A.
;   adc a,0   ;We don't need to worry abput overflow here :)
;
; A_mod_3:
; ;destroys HL, returns A mod 3 in A
; ;97+{0,2} + {0,8} + {0,1}
; ;min: 97
; ;max: 108
; ;avg: 102.5
;
; ;A mod 3 is equal to adding the upper and lower nibble of A mod 3
; ;For example, if A=16u+l, then A mod 3 == 16u+l mod 3 == u+l
; ;So add the upper and lower nibble
;   ld l,a  ;save a copy of a
;   add a,a
;   add a,a
;   add a,a
;   add a,a
;   add a,l
;
; ; If there was overflow, again, add 1. However, our number is shifted up by 4,
; ; so we need to add 1<<4 == 16
;   jr nc,$+4
;   add a,16
;
; ; Now our number is in the upper 4 bits of A. We need to add the top 2 bits to
; ; the preceding 2 bits
;
;   ld l,a
;   add a,a
;   add a,a
;
; ; Note that now we might have some garbage bits in the middle 4 bits of A,
; ; overlapping two garbage bits in L. We'll need to clear out bits to avoid
; ; issues. It is convenient to use a mask of %11000000
;   ld h,%11000000
;   and h
;   add a,l
;
; ;Now if there was overflow, add 1<<6 == $40. H "happens" to be -$40, so we can
; ;do this by subtracting h
;   jr nc,$+3
;   sub h
;
; ;Now finally, mask out all but those upper two bits
;   and h
;
; ; At this point, we can stop if we only need to test divisibility
; ; If the parity is even, then we have to do (0 mod 3) or (3 mod 3), both of
; ; which are 0, indicating divisibility by 3. If we have odd parity, then the
; ; upper two bits are 10 or 01, both of which are not 0 mod 3.
; ; basically, pe==divisible, po==not divisible.
; ;
; ; But, to get full modulo, shift those uppertwo bits into the lower two bits
;   rlca
;   rlca
;   ret po
; ; And make sure to set A to 0 if it was 0 or 3 :)
;   xor a
;   ret
