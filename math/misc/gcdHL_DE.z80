gcdHL_DE:
;gcd(HL,DE)->HL
;Output:
;   B=0
;   HL is the GCD of the inputs
;Destroys:
;   A,DE
;     DE is guaranteed 0 unless the output is 0 (which only happens if one of the inputs is 0).
;Uses the binary GCD algorithm
;65 bytes

;B is our cofactor-of-2 counter
    ld b,0

;If HL=0, return 0
    ld a,h \ or l \ ret z

;If DE=0, return 0
    ex de,hl
    ld a,h \ or l \ jr nz,gcd_test_cofactor_of_2
    ret

gcd_cofactor_2_loop:
    inc b
    srl h \ rr l
    srl d \ rr e
gcd_test_cofactor_of_2:
    inc b
    ld a,e
    or l
    rra
    jr nc,gcd_cofactor_2_loop

gcd_remove_factors_of_2_op2:
    srl h \ rr l \ jr nc,gcd_remove_factors_of_2_op2
    adc hl,hl
    jr gcd_swap_ops

gcd_swap_ops_negate:
;At this point, HL needs to be negated and swapped with DE
    xor a \ sub l \ ld l,a \ sbc a,a \ sub h \ ld h,a
gcd_swap_ops:
    ex de,hl
gcd_remove_factors_of_2_op1:
    srl h \ rr l \ jr nc,gcd_remove_factors_of_2_op1
    adc hl,hl
    sbc hl,de
    jr c,gcd_swap_ops_negate
    jp nz,gcd_remove_factors_of_2_op1

;DE is the GCD, need to shift it left B-1 times.
    ex de,hl
    dec b
    ret z
    add hl,hl \ djnz $-1
    ret
