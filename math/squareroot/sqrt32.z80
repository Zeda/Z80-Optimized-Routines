sqrt32:
;Input: HLDE
;Output: DE is the sqrt, AHL is the remainder
;speed: 238+{0,1}+{0,44}+sqrtHL+3*sqrt32sub_2+sqrt32_iter15
;min: 1260
;max: 1506
;avg: 1377.75

  push de
  call sqrtHL
  pop bc
  add a,a
  ld e,a
  jr nc,+_
  inc d
_:

  ld a,b
  call sqrt32sub_2
  call sqrt32sub_2
;Now we have four more iterations
;The first two are no problem
  ld a,c
  call sqrt32sub_2

;On the next iteration, HL might temporarily overflow by 1 bit
  call sqrt32_iter15

;On the next iteration, HL is allowed to overflow, DE could overflow with our current routine, but it needs to be shifted right at the end, anyways
sqrt32_iter16:
  add a,a
  ld b,a        ;either 0x00 or 0x80
  adc hl,hl
  rla
  adc hl,hl
  rla
;AHL - (DE+DE+1)
  sbc hl,de \ sbc a,b
  inc e
  or a
  sbc hl,de \ sbc a,b
  ret p
  add hl,de
  adc a,b
  dec e
  add hl,de
  adc a,b
  ret

sqrt32sub_2:
;min: 185cc
;max: 231cc
;avg: 208cc
  call +_

_:
;min: 84cc
;max: 107cc
;avg: 95.5cc

  sll e \ rl d
  add a,a \ adc hl,hl
  add a,a \ adc hl,hl

  sbc hl,de
  inc e
  ret nc
  dec e
  add hl,de
  dec e
  ret

sqrt32_iter15:
;91+{8,0+{0,23}}
;min: 91cc
;max: 114cc
;avg: 100.75cc

  sll e \ rl d      ;sla e \ rl d \ inc e
  add a,a
  adc hl,hl
  add a,a
  adc hl,hl       ;This might overflow!
  jr c,sqrt32_iter15_br0
;
  sbc hl,de
  inc e
  ret nc
  dec e
  add hl,de
  dec e
  ret
sqrt32_iter15_br0:
  or a
  sbc hl,de
  inc e
  ret
