Log_2_88_size:
;Inputs:
;     HL is an unsigned 8.8 fixed point number.
;Outputs:
;     HL is the signed 8.8 fixed point value of log base 2 of the input.
;Example:
;     pass HL = 3.0, returns 1.58203125 (actual is ~1.584962501...)
;averages about 39 t-states slower than original
;62 bytes
     ex de,hl
     ld hl,0
     ld a,d
     ld c,8
     or a
     jr z,DE_lessthan_1
     srl d
     jr z,logloop-1
     inc l
     rr e
     jr $-7
DE_lessthan_1:
     ld a,e
     dec hl
     or a
     ret z
     inc l
     dec l
     add a,a
     jr nc,$-2
     ld e,a

     inc d
logloop:
     add hl,hl
     push hl
     ld h,d
     ld l,e
     ld a,e
     ld b,8

     add hl,hl
     rla
     jr nc,$+5
       add hl,de
       adc a,0
     djnz $-7

     ld e,h
     ld d,a
     pop hl
     rr a         ;this is NOT supposed to be rra, we need the z flag affected
     jr z,$+7
       srl d
       rr e
       inc l
     dec c
     jr nz,logloop
     ret
