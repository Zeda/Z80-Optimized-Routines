HL_Div_5_round:
;210cc or 220cc
    xor a
    ld d,h \ ld e,l \ ld b,a
    add hl,hl \ rla
    add hl,de \ adc a,b
    ld d,h \ ld e,l \ ld c,a
    add hl,hl \ rla
    add hl,hl \ rla
    add hl,hl \ rla
    add hl,hl \ rla
    add hl,de \ adc a,c
    ld d,a \ ld e,h
    add hl,de \ adc a,b
    ld d,a \ ld e,h
    add a,l
    ex de,hl
    rla \ rla \ and 3 \ rra
    adc a,b
    add a,l
    ld l,a
    ret nc
    inc h
    ret
