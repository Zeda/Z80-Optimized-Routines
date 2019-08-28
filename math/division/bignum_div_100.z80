bignum_div_100:
;Input:
;   HL points to the bignum (1 byte size prefix (0 -> 1 byte, 1 -> 2 bytes, n-1 -> n bytes), n subsequent bytes)
;Output:
;   bignum is divided in-place, not renormalized
;   A is the remainder
;   BC is 100
    ld c,100
bignum_div_C:
;Note: C<128
    ld b,(hl)
    inc hl
    ld a,(hl)
    ld h,-1
    inc h \ sub c \ jr nc,$-2
    add a,c
    ld (hl),a
    inc b
    dec b
    ret z
_:
    inc hl
    ld e,(hl)
    sla e \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc e
    sla e \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc e
    sla e \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc e
    sla e \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc e
    sla e \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc e
    sla e \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc e
    sla e \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc e
    sla e \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc e
    ld (hl),a
    djnz -_
    ret
