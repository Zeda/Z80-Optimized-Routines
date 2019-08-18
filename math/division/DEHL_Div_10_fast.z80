DEHL_Div_10:
;Inputs:
;     DEHL
;Outputs:
;     DEHL is the quotient
;     A is the remainder
;     B is the remainder
;     C is 10
;1300cc~1329cc
;49 bytes
    xor a
    ld bc,05F6h
    rl d \ rla
    rl d \ rla
    rl d \ rla
    rl d \ rla \ add a,c \ jr c,$+3 \ sub c \ djnz $-7
    ld b,8
    rl e \ rla \ add a,c \ jr c,$+3 \ sub c \ djnz $-7
    ld b,8
    rl h \ rla \ add a,c \ jr c,$+3 \ sub c \ djnz $-7
    ld b,8
    rl l \ rla \ add a,c \ jr c,$+3 \ sub c \ djnz $-7

    adc hl,hl
    rl e
    rl d
    ret
