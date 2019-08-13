AL_div_100:
;Divides a 16-bit integer by 100, where A holds the upper 8 bits and L holds the lower
;Result is in HL, A is the remainder
;min:256
;max:329
;avg:305.5625cc
    ld c,100
AL_Div_C:
;Note: C<128
    ld h,-1
    inc h \ sub c \ jr nc,$-2
    add a,c
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ jr c,$+4 \ sub a,c \ inc l
    sla l \ rla  \ cp c \ ret c \ sub a,c \ inc l
    ret