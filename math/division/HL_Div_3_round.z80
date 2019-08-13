HL_Div_3_round:
;205cc or 215cc
    xor a \ ld d,h \ ld e,l
    add hl,hl \ rla
    add hl,hl \ rla
    add hl,de
    ld d,h \ ld e,l \ ld b,a
    add hl,hl \ rla
    add hl,hl \ rla
    add hl,hl \ rla
    add hl,hl \ rla
    add hl,de \ adc a,bas
    ld d,h \ ld e,l \ ld b,a
    ld d,a \ ld e,h \ add hl,de
    adc a,0
    sla l
    ld l,h
    ld h,a
    ret nc
    inc hl
    ret    

