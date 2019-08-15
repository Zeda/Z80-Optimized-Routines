SqrtL:
;Inputs:
;     L is the value to find the square root of
;Outputs:
;      C is the result
;      B,L are 0
;     DE is not changed
;      H is how far away it is from the next smallest perfect square
;      L is 0
;      z flag set if it was a perfect square
;Destroyed:
;      A
     ld bc,400h       ; 10    10
     ld h,c           ; 4      4
sqrt8Loop:            ;
     add hl,hl        ;11     44
     add hl,hl        ;11     44
     rl c             ; 8     32
     ld a,c           ; 4     16
     rla              ; 4     16
     sub a,h          ; 4     16
     jr nc,$+5        ;12|19  48+7x
       inc c
       cpl
       ld h,a
     djnz sqrt8Loop   ;13|8   47
     ret              ;10     10
;287+7x, x is the number of bits in the result
;min: 287
;max: 315
;19 bytes
