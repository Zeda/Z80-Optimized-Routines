ALDEIX_div_100:
;Divides a 48-bit integer by 100, where A holds the upper 8 bits and L holds the next 8, followed by DE and IX
;Result is in HLDEIX, A is the remainder
    ld c,100
ALDEIX_Div_C:
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
    call +_
    push hl
    push ix
    pop de
    ld l,d
    call +_
    ld h,l
    ld l,e
    call +_
    pop de
    ex (sp),ix
    pop hl
    ret
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