;Written by calc84maniac, based on a routine from Zeda
;===============================================================
HL_SDiv_BC:
;===============================================================
;Performs HL/BC
;Speed:   1168 to 1318 cycles depending on how many set bits in the result
;         add 19 if HL is negative
;         add 19 if BC is positive
;         add another 28 if only one is negative
;Size:    54 bytes
;         **31 bytes larger than the regular HL_Div_BC
;Inputs:
;     HL is the numerator
;     BC is the denominator
;Outputs:
;     HL is the quotient
;     DE is the remainder
;     BC = -abs(BC)
;===============================================================
     ld a,h
     xor b
     push af
absHL:
     add hl,hl
     jr nc,negabsBC
     xor a \ sub l \ ld l,a
     sbc a,a \ sub h \ ld h,a
negabsBC:
     bit 7,b
     jr nz,$+8
     xor a \ sub c \ ld c,a
     sbc a,a \ sub b \ ld b,a
       ex de,hl
       xor a
       ld h,a
       ld l,a
       ld a,15
Div_Loop_1:
         rl e \ rl d
         adc hl,hl
         add hl,bc
         jr c,$+4
          sbc hl,bc
         dec a
         jr nz,Div_Loop_1
       ex de,hl
       adc hl,hl
       pop af \ ret p
     xor a \ sub l \ ld l,a
     sbc a,a \ sub h \ ld h,a
     ret
