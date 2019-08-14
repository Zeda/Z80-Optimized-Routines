L_sqrd:
;Input: L
;Output: L*L->A
;147 t-states
;36 bytes
    ld b,l
;First iteration, get the lowest 3 bits of -x^2
    sla l
    rrc b
    sbc a,a
    or l
    ld c,a
;second iteration, get the next 2 bits of -x^2
    rrc b
    sbc a,a
    xor l
    and $F8
    add a,c
    ld c,a
;third iteration, get the next 2 bits of -x^2
    sla l
    rrc b
    sbc a,a
    xor l
    and $E0
    add a,c
    ld c,a
;fourth iteration, get the eight bit of x^2
    sla l
    rrc b
    sbc a,a
    xor l
    and $80
    sub c
    ret
