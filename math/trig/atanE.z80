atanE:
;returns H=256*arctan(E/256)
;min: 496cc
;max: 539cc
;avg: 517.5cc
;multiply E by 201
  ld d,0
  ld h,d
  ld l,e
  add hl,hl
  add hl,de
  add hl,hl
  add hl,hl
  add hl,hl
  add hl,de
  add hl,hl
  add hl,hl
  add hl,hl
  add hl,de
  ld b,h
  ld c,l

;E*(256-E)
  xor a
  ld d,a
  sub e
  ld h,a
  ld l,d
  sla h \ jr nc,$+3 \ ld l,e
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl \ jr nc,$+3 \ add hl,de
;.HL*70
  ld d,h
  ld e,l
  xor a
  add hl,hl
  add hl,hl \ rla   ;rla needed for the case when input = 128 :(
  add hl,hl \ rla
  add hl,hl \ rla
  add hl,de \ adc a,0
  add hl,hl \ rla
  add hl,de \ adc a,0
  add hl,hl \ rla
  ld l,h
  ld h,a
  add hl,bc
  ret
