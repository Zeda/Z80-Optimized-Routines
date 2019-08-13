HL_Div_384:
;223cc
  ;(HL+HL*5*17*2)/256
  push hl
  ld b,h
  ld c,l
  xor a
  add hl,hl \ rl a
  add hl,hl \ rl a
  add hl,bc \ adc a,0
  ld d,a
  ld b,h
  ld c,l
  add hl,hl \ rl a
  add hl,hl \ rl a
  add hl,hl \ rl a
  add hl,hl \ rl a
  add hl,bc \ adc a,d
  add hl,hl \ rla
  pop de
  add hl,hl \ rl a
  sla l
  adc a,0
  ret