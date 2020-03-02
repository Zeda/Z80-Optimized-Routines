uint32tostr_dec:
;Inputs:
;     DEHL is the number to display
;     IX points to the end of the output location
;Outputs:
;     A, B, D, E is 0
;     C is 10
;     HL points to the base-10 string.
;NOTE: This does not put a 0 byte at the end
  ld c,10
uint32tostr:
;Inputs:
;     C is the base
;     DEHL is the number to display
;     IX points to the end of the output location
;       NOTE: If you want the string to be null-terminated, you'll have to
;             write a 0 to IX yourself.
;Outputs:
;     A, B, D, E is 0
;     C is not changed
;     HL points to the string
;NOTE: This does not put a 0 byte at the end
    ld b,32
    xor a
_:
    add hl,hl
    rl e
    rl d
    rla
    cp c
    jr c,$+4
    inc l
    sub c
    djnz -_
    add a,30h
    cp 3Ah
    jr c,+_
    add a,7
_:
    dec ix
    ld (ix),a
    ld a,h
    or l \ or d \ or e
    jr nz,uint32tostr
    push ix
    pop hl
    ret
