;Requires:
;   mul16
;     Inputs: BC,DE
;     Output: DEHL
;   8 bytes at z32_0 (you must define this)


mul32:
;max: 703cc  + 3*mul16
;     2704cc
;min: 655cc  + 3*mul16
;     1297cc
;avg: 673.25cc+3*mul16
;     2307.911cc
;DEHL * BCIX ==> z32_0
z32_2 = z32_0+4

  push de
  push bc
  push hl
  push ix
  call mul16  ;DEHL
  ld (z32_2),hl
  ld (z32_2+2),de

  pop de
  pop bc
;  push bc
  push de
  call mul16  ;DEHL
  ld (z32_0),hl
  ld (z32_0+2),de

  pop de    ;low word
;  pop bc    ;low word
  pop hl
  xor a
  sbc hl,de
  jr nc,+_
  sub l
  ld l,a
  sbc a,a
  sub h
  ld h,a
  xor a
  inc a
_:
  ex de,hl
  pop hl
  sbc hl,bc
  jr nc,+_
  ld b,a
  xor a
  sub l
  ld l,a
  sbc a,a
  sub h
  ld h,a
  ld a,b
  inc a
_:
  ld b,h
  ld c,l
  push af
  call mul16
  pop af    ;holds the sign in the low bit
  rra
  jr c,mul32_add
;need to perform z0+z2-result
  push de
  push hl
  xor a
  ld hl,(z32_0)
  ld bc,(z32_2)
  add hl,bc
  ex de,hl
  ld hl,(z32_0+2)
  ld bc,(z32_2+2)
  adc hl,bc
  rla
;now need to subtract
  ex de,hl
  pop bc
  sbc hl,bc
  ex de,hl
  pop bc
  sbc hl,bc
  sbc a,0
;A:HL:DE is the result, need to add to z32_0+2
mul32_final:
  ld bc,(z32_0+2)
  ex de,hl
  add hl,bc
  ld (z32_0+2),hl
  ld hl,(z32_2)
  adc hl,de
  ld (z32_2),hl
  ld hl,z32_2+2
  adc a,(hl)
  ld (hl),a
  ret nc
  inc hl
  inc (hl)
  ret
mul32_add:
;add to the current result
  xor a
  ld bc,(z32_0)
  add hl,bc
  ex de,hl
  ld bc,(z32_0+2)
  adc hl,bc
  rla
  ex de,hl
  ld bc,(z32_2)
  add hl,bc
  ex de,hl
  ld bc,(z32_2+2)
  adc hl,bc
  adc a,0
  jp mul32_final
