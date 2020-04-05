;Reverses the bits in HL
;author: calcmaniac84

reverseHL:
;28 bytes and 112 cycles (with RET: 29 bytes, 122cc)
  ld a,l
  rla
  rr h
  rla
  rr h
  rla
  rr h
  rla
  rr h
  rla
  rr h
  rla
  rr h
  rla
  rr h
  rla
  rr h
  rla
  rrca
  ld l,a
  ret
