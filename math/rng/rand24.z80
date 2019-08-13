rand24:
;;219cc
#ifdef smc
seed1_0=$+1
    ld hl,12345
seed1_1=$+1
    ld a,67
#else
    ld hl,(seed1_0)
    ld a,(seed1_1)
#endif
    ld b,h
    ld c,l
    ld d,a
    add hl,hl \ rla
    add hl,hl \ rla
    inc l
    add hl,bc \ adc a,0
    ld (seed1_0),hl
    ld (seed1_1),a
    ld c,b
    ld b,a
#ifdef smc
seed2_0=$+1
    ld hl,65432
seed2_1=$+1
    ld a,10
#else
    ld hl,(seed2_0)
    ld a,(seed2_1)
#endif
    add hl,hl
    rla
    ld (seed2_1),a
    sbc a,a
    and %10000111
    xor l
    ld l,a
    ld (seed2_0),hl
    add hl,bc
    ret
