
ln_88:
;Input: HL is a fixed point number
;Output: ln(H.L)->H.L
;Speed: Avg: 340+(325 worst case)
   call lg_88
   ;now signed multiply HL by 355, then divide by 2 (rounding)
    ld de,0
    bit 7,h
    jr z,$+9
    dec e \ xor a \ sub l \ ld l,a
    sbc a,a \ sub h \ ld h,a
    ld b,h
    ld c,l
    xor a
   add hl,hl
      add hl,hl \ rla
   add hl,bc \ adc a,d
   add hl,hl \ rla
   add hl,bc \ adc a,d
   add hl,hl \ rla
   add hl,hl \ rla
   add hl,hl \ rla
   add hl,hl \ rla
   add hl,bc \ adc a,d
   add hl,hl \ rla
   add hl,bc \ adc a,d
    sra a \ rr h
    ld l,h
    ld h,a
    inc e
    ret nz
    xor a \ sub l \ ld l,a
    sbc a,a \ sub h \ ld h,a
    ret
