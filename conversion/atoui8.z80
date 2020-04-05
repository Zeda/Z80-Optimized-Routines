atoui8:
strtob:
;Input:
;   HL is a string, terminated by a non-numeric ASCII char
;Output:
;   A has the 8-bit value
strtob:
    xor a
    jr inloop
loop:
    ld e,a
    ld a,d
    add a,a     ;double our accumulator
    add a,a     ;double again (now x4)
    add a,d     ;add the original (now x5)
    add a,a     ;double again (now x10)
    add a,e     ;add in the incoming digit
    inc hl
inloop:
    ld d,a
    ld a,(hl)
    sub '9'+1
    add 10
    jr c,loop
    ld a,d
    ret
