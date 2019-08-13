div9:
;HL/9 --> A, HL<256*9
  inc hl
  ld d,h
  ld e,l
  add hl,hl
  add hl,de
  add hl,hl
  add hl,de
  ld e,0
  ld d,l
  ld a,h
  add hl,hl
  add hl,hl
  add hl,de
  adc a,e
  add hl,hl
  rla
  add hl,hl
  rla
  ret
