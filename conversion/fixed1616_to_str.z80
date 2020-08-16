#ifndef included_fixed1616_to_str
#define included_fixed1616_to_str

fixed1616_to_str:
;Input:
;   DE.BC is the float
;   HL points to where to write the string (at least 14 bytes)
;Output:
;   HL points to the string (not necessarily matching the input)
  bit 7,d
  jr z,+_
  xor a
  sub c
  ld c,a
  ld a,0
  sbc a,b
  ld b,a
  ld a,0
  sbc a,e
  ld e,a
  sbc a,a
  sub d
  ld d,a
  inc hl
_:
  push bc
  push af   ;z flag set if no negative sign
  call itoa_16
  pop af
  jr z,+_
  dec hl
  ld (hl),$1A
_:
  pop de
  ld a,d
  or e
  ret z
  push hl

;find the end of the string
  xor a
  cpir

  dec hl
  ld (hl),'.'
  inc hl
  ex de,hl
;DE points to the output
;HL is the fractional part
  call fixed1616_to_str_sub
  call fixed1616_to_str_sub
  call fixed1616_to_str_sub
  call fixed1616_to_str_sub
  call fixed1616_to_str_sub
  call fixed1616_to_str_sub
  ex de,hl
  ld a,'0'
_:
  dec hl
  cp (hl)
  jr z,-_
  inc hl
  ld (hl),0
  pop hl
  ret

fixed1616_to_str_sub:
  xor a
  ld b,h
  ld c,l
  add hl,hl \ rla
  add hl,hl \ rla
  add hl,bc \ adc a,$18
  add hl,hl \ rla
  ld (de),a
  inc de
  ret

#endif
