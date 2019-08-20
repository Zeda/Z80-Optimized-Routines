;Signed division CHL/DE by Zeda, inspired by code from matrefeytontias.

;signed CHL/DE
sdiv24_16:
;signed CHL/DE ==> CHL, |remainder| is DE

;Get the sign of the result
  ld a,c
  xor d
  push af

;Make BHL positive
  xor d
  jp p,+_
  xor a
  sub l
  ld l,a
  ld a,0
  sbc a,h
  ld h,a
  sbc a,a
  sub c
  ld c,a
_:

;make DE negative
  bit 7,d
  jr z,+_   ;setting DE negative
  xor a
  sub e
  ld e,a
  sbc a,a
  sub d
  ld d,a
  ld a,c
_:

  ld b,24
  push hl
  pop ix
  ld hl,0

div2416loop:
  add ix,ix
  rla
  adc hl,hl
  add hl,de
  jr c,+_
  sbc hl,de
  .db $DA     ;start or `jp c,**`
_:
  inc ixl
  djnz div2416loop
  ld c,a
  ex de,hl    ;DE is remainder

  push ix
  pop hl

;restore sign
  pop af
  ret p
  xor a
  sub l
  ld l,a
  ld a,b
  sbc a,h
  ld h,a
  sbc a,a
  sub c
  ld c,a
  ret
