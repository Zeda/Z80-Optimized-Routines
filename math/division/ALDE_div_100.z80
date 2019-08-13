ALDE_div_100:
;Divides a 32-bit integer by 100, where A holds the upper 8 bits and L holds the next 8, followed by DE
;Result is in DEHL, A is the remainder
    ld c,100
ALDE_Div_C:
;Note: C<128
    ld h,-1
    inc h \ sub c \ jr nc,$-2
    add a,c
    call +_
    push hl
    ld l,d
    call +_
    ld h,l
    ld l,e
    pop de
_:
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ ret c \ sub a,c \ inc l
    ret