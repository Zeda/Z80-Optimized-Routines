atoui32:
;===============================================================
;Input:
;     DE points to the base 10 number string in RAM.
;Outputs:
;     HLIX is the 32-bit value of the number
;     DE points to the byte after the number
;     BC points to the start of the number
;     z flag means it ended on a decimal point.
;Destroys:
;     A (actually, add 30h and you get the ending token)
;     BC
;===============================================================
  ld hl,0
  ld ix,0
  push de   ;save the pointer
  jr atoui16_start
_:
  inc de
  ld b,ixh
  ld c,ixl
  push hl
  add ix,ix \ adc hl,hl
  add ix,ix \ adc hl,hl
  inc ix
  dec ix 
  add ix,bc \ pop bc \ adc hl,bc
  add ix,ix \ adc hl,hl
  add a,ixl
  ld ixl,a
  jr nc,atoui16_start
  inc ixh
  jr nz,atoui16_start
  inc hl
atoui16_start:
  ld a,(de)
  sub 30h
  cp 10
  jr c,-_
  pop bc
  ret
