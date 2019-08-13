DEHL_Div_10:
;Inputs:
;     DEHL
;Outputs:
;     DEHL is the quotient
;     A is the remainder
;     B is the remainder
;     C is 10
;912cc~941cc

    xor a
    ld c,10
    rl d \ rla
    rl d \ rla
    rl d \ rla
    rl d \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl d \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl d \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl d \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl d \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl e \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl e \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl e \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl e \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl e \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl e \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl e \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl e \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl h \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl h \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl h \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl h \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl h \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl h \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl h \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl h \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl l \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl l \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl l \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl l \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl l \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl l \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl l \ rla \ sub c \ jr nc,$+3 \ add a,c
    rl l \ rla \ sub c \ jr nc,$+3 \ add a,c
    ld b,a
    ld a,l \ rra \ ccf \ ld l,a
    ld a,h \ rra \ ccf \ ld h,a
    ld a,e \ rra \ ccf \ ld e,a
    ld a,d \ rra \ ccf \ ld d,a
    ld a,b
    ret
