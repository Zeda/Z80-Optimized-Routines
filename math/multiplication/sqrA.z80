sqrA:
;A*A->A
;Destroys: HL
;76cc or 79cc or 82cc
;Avg: 79cc
;51 bytes
    add a,a
    add a,a
    jr nc,$+4
    neg
    rrca
    rrca
    ld l,a
    srl l
    ld h,sqrLUT/256
    jr c,$+4
    neg
    add a,(hl)
    ret
sqrLUT:
;MUST BE ALIGNED to a 256-byte boundary.
;Can use:
;  #if 0!=$&255
;  .fill 256-($&255),0
;  #endif
.db $00,$06,$14,$2A,$48,$6E,$9C,$D2
.db $10,$56,$A4,$FA,$58,$BE,$2C,$A2
.db $20,$A6,$34,$CA,$68,$0E,$BC,$72
.db $30,$F6,$C4,$9A,$78,$5E,$4C,$42
