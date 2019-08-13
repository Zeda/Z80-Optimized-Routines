BC_Div_DE:
    ld hl,0
    inc d
    dec d
    jr z,smalldiv
    ld l,b
    ld b,h
nextpart:
    ld a,c
    rla \ adc hl,hl \ sbc hl,de \ jr nc,$+3 \ add hl,de
    rla \ adc hl,hl \ sbc hl,de \ jr nc,$+3 \ add hl,de
    rla \ adc hl,hl \ sbc hl,de \ jr nc,$+3 \ add hl,de
    rla \ adc hl,hl \ sbc hl,de \ jr nc,$+3 \ add hl,de
    rla \ adc hl,hl \ sbc hl,de \ jr nc,$+3 \ add hl,de
    rla \ adc hl,hl \ sbc hl,de \ jr nc,$+3 \ add hl,de
    rla \ adc hl,hl \ sbc hl,de \ jr nc,$+3 \ add hl,de
    rla \ adc hl,hl \ sbc hl,de \ jr nc,$+3 \ add hl,de
    cpl
    ld c,a
    ret
smalldiv:
    xor a
    rl b \ rla \ sub e \ jr nc,$+3 \ add a,e
    rl b \ rla \ sub e \ jr nc,$+3 \ add a,e
    rl b \ rla \ sub e \ jr nc,$+3 \ add a,e
    rl b \ rla \ sub e \ jr nc,$+3 \ add a,e
    rl b \ rla \ sub e \ jr nc,$+3 \ add a,e
    rl b \ rla \ sub e \ jr nc,$+3 \ add a,e
    rl b \ rla \ sub e \ jr nc,$+3 \ add a,e
    rl b \ rla \ sub e \ jr nc,$+3 \ add a,e
    ld l,a
    ld a,b
    cpl
    ld b,a
    jp nextpart
