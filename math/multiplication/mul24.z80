;And mul24 needs 6 bytes at var48 defined.

mul24:
;BDE*CHL -> HLBCDE
;155 bytes
;402+3*C_Times_BDE
;fastest:1201cc
;slowest:1753cc
;avg: 1464.9033203125cc (1464+925/1024)
;min: 825cc
;max: 1926cc
;avg: 1449.63839751681cc

    push bc
    ld c,l
    push hl
    call C_Times_BDE
    ld (var48),hl
    ld l,a
    ld h,c
    ld (var48+2),hl

    pop hl
    ld c,h
    call C_Times_BDE
    push bc
    ld bc,(var48+1)
    add hl,bc
    ld (var48+1),hl
    pop bc
    ld b,c
    ld c,a
    ld hl,(var48+3)
    ld h,0
    adc hl,bc
    ld (var48+3),hl

    pop bc
    call C_Times_BDE
    ld de,(var48+2)
    add hl,de
    ld (var48+2),hl
    ld d,c
    ld e,a
    ld b,h
    ld c,l
    ld hl,(var48+4)
    ld h,0
    adc hl,de
    ld de,(var48)
    ret
