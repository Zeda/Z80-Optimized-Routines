sqrtDE:
;returns HL as the sqrt, DE as the remainder
;33 bytes
;min: 928cc
;max: 1120cc
;avg: 1024cc
;928+8{24,0}

  ld b,$80
  xor a
  ld h,a
  ld l,a
sqrt_loop:
  srl b
  rra
  ld c,a
  add hl,bc
  ex de,hl
  sbc hl,de
  jr nc,+_
  add hl,de
  ex de,hl
  or a
  sbc hl,bc
  .db $DA   ;start of jp c,** which is 10cc to skip the next two bytes.
_:
  ex de,hl
  add hl,bc
  srl h
  rr l
  srl b
  rra
  jr nc,sqrt_loop
  ret
