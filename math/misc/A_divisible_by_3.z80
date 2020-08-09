A_divisible_by_3:
;Inputs: A
;Outputs: pe if A was divisible by 3, po if A was not divisible by 3
;Destroys: HL
;88+{0,2}+{0,1}
;min: 88
;max: 91
;avg: 89.5
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
  ret
