HL_divisible_by_3:
;Inputs: HL
;Outputs: pe if HL was divisible by 3, else po.
;Destroys: HL
;103+{0,2}+{0,1}
;min: 103
;max: 106
;avg: 104.5
  ld a,h
  add a,l
  adc a,0

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
