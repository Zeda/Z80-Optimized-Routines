HL_Div_5:
;HL/5
;HL/4+HL*3*17*257
;234cc to 245cc
  xor a
  ld b,h
  ld c,l
  ld d,a
  add hl,hl \ rla
  add hl,bc \ adc a,d   ;3
  add hl,hl \ rla       ;6
  add hl,hl \ rla       ;12
  add hl,hl \ rla       ;24
  add hl,bc \ adc a,d   ;25
  add hl,hl \ rla       ;50
  add hl,bc \ adc a,d   ;51
;AHL0+AHL+BC/2
;AHL*257/256 =AHL+A
  srl b \ rr c
  srl b \ rr c
  ld d,a
  ld a,b
  add a,l
  ld b,a
  ld e,h
  jr nc,$+3
  inc de
  add hl,bc
  ld a,d
  add a,e
  ld e,a
  ret nc
  inc d
  ret
