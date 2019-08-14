L_To_BCD:
;Unrolled
;Converts the 8-bit register L to binary coded decimal
;Digits stored in LA (A has the lower 2 digits, L the upper).
;Inputs: L is the 8-bit unsigned int to convert
;Output: A has the lower 2 digits (in BCD form), L has the upper
;Destroys: H,F
;141cc
;27 bytes
    ld h,0
    add hl,hl
    add hl,hl
    add hl,hl
    add hl,hl
    ld a,h \ daa  \ rl l
    adc a,a \ daa \ rl l
    adc a,a \ daa \ rl l
    adc a,a \ daa \ rl l
    adc a,a \ daa \ rl l
    ret
