A_mod_3:
;destroys HL, returns A mod 3 in A
;97+{0,2} + {0,8} + {0,1}
;min: 97
;max: 108
;avg: 102.5
  ld h,$C0
  ld l,a  ;save a copy of a
  add a,a
  add a,a
  add a,a
  add a,a
  add a,l
  jr nc,$+4
  add a,16

  ld l,a
  add a,a
  add a,a
  and h
  add a,l

  jr nc,$+3
  sub h

  and h
  rlca
  rlca
  ret po
  xor a
  ret
