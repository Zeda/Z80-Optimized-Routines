;This multiplies two 64-bit integers and returns a 128-bit result.
;This requires the following routines:
;   mul32
;       Inputs: DEHL, BCIX
;       Output: stored at z32_0, little-endian

mulfixed16_16:
;Multiplies DE.HL by BC.IX, stores the result in DE.HL
; First, find out if the output is positive or negative
  ld a,d
  xor b
  push af   ;sign bit is the result sign bit

; Now make sure the inputs are positive
  xor b     ;A now has the value of D, since I XORed it with B twice (cancelling)
  jp p,+_   ;if Positive, don't negate
  xor a
  sub l
  ld l,a
  ld a,0
  sbc a,h
  ld h,a
  ld a,0
  sbc a,e
  ld e,a
  sbc a,a
  sub d
  ld d,a
_:
  bit 7,b
  jr z,+_
  xor a
  sub ixl
  ld ixl,a
  ld a,0
  sbc a,ixh
  ld ixh,a
  ld a,0
  sbc a,c
  ld c,a
  sbc a,a
  sub b
  ld b,a
_:

; Now we multiply
  call mul32

;We should check for overflow. If the upper two bytes are non-zero, we will set the result to 0x7FFFFFFF
  ld hl,(z32_0+6)
  ld a,h
  or l

;Get the middle four bytes and put them in DEHL
  ld hl,(z32_0+2)
  ld de,(z32_0+4)

;Maybe we need to set the result to 0x7FFFFFFF
  jr z,+_
  ld de,$7FFF
  ld h,e
  ld l,e
_:

; Now we need to restore the sign
  pop af
  ret p    ;don't need to do anything, result is already positive
  xor a
  ld b,a
  sub l
  ld l,a
  ld a,b
  sbc a,h
  ld h,a
  ld a,b
  sbc a,e
  ld e,a
  sbc a,a
  sub d
  ld d,a
  ret
