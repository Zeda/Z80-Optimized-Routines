;Adds two, little-endian 16-digit BCD integers (8 bytes)

addBCD_16:
;Input:
;   HL points to one BCD integer
;   DE points to another BCD integer
;Output:
;   The sum is wrriten over the integer at HL.
;   HL and DE point to the last digit of their integers.
;46 bytes, 284cc
    ld a,(de) \ add a,(hl) \ daa \ ld (de),a \ inc hl \ inc de
    ld a,(de) \ adc a,(hl) \ daa \ ld (de),a \ inc hl \ inc de
    ld a,(de) \ adc a,(hl) \ daa \ ld (de),a \ inc hl \ inc de
    ld a,(de) \ adc a,(hl) \ daa \ ld (de),a \ inc hl \ inc de
    ld a,(de) \ adc a,(hl) \ daa \ ld (de),a \ inc hl \ inc de
    ld a,(de) \ adc a,(hl) \ daa \ ld (de),a \ inc hl \ inc de
    ld a,(de) \ adc a,(hl) \ daa \ ld (de),a \ inc hl \ inc de
    ld a,(de) \ adc a,(hl) \ daa \ ld (de),a
    ret
