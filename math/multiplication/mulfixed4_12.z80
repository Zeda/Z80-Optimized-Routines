;Requires:
;   mul16
;     Inputs: BC,DE
;     Output: DEHL

mulfixed4_12:
;Multiplies 4.12 fixed point numbers.
;Inputs: HL is the first fixed-point multiplicand
;        DE is the second fixed-point multiplicand
;Output: HL is the fixed-point output
;Overflow is stored as 0x7.FFF or 0x8.001 depending on positive or negative
; First, find out if the output is positive or negative
  ld a,h
  xor d
  push af   ;sign bit is the result sign bit

; Now make sure the inputs are positive
  xor d     ;A now has the value of H, since I XORed it with D twice (cancelling)
  jp p,+_   ;if Positive, don't negate
  xor a
  sub l
  ld l,a
  sbc a,a
  sub h
  ld h,a
_:
  bit 7,d
  jr z,+_
  xor a
  sub e
  ld e,a
  sbc a,a
  sub d
  ld d,a
_:

; Now we need to put DE in BC to use mul16
  ld b,h
  ld c,l
  call mul16

;The result doesn't need the top 4 bits or bottom 12 bits.
;We'll hold onto the top 4 bits to check overflow, though.
;Currently we need to shift DEH left by 4 bits and keep DE, or right by 12 bits and keep HL.
  ld a,h    ;we'll actually be moving the discared bits into A
  and $F0
  ex de,hl
  rla \ adc hl,hl
  rla \ adc hl,hl
  rla \ adc hl,hl
  rla \ adc hl,hl
  adc a,a

;if A is non-zero, we have overflow
  jr z,+_
  ld hl,$7FFF
_:

; Now we need to restore the sign
  pop af
  ret p    ;don't need to do anything, result is already positive
  xor a
  sub l
  ld l,a
  sbc a,a
  sub h
  ld h,a
  ret
