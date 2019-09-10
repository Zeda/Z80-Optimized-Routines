sqrtHLIX:
;Input: HLIX
;Output: DE is the sqrt, AHL is the remainder
;speed: 751+6{0,6}+{0,3+{0,18}}+{0,38}+sqrtHL
;min: 1103
;max: 1237
;avg: 1165.5
;166 bytes

  call sqrtHL   ;expects returns A as sqrt, HL as remainder, D = 0
  add a,a
  ld e,a
  rl d

  ld a,ixh
  sll e \ rl d
  add a,a \ adc hl,hl
  add a,a \ adc hl,hl
  sbc hl,de
  jr nc,+_
  add hl,de
  dec e
  .db $FE     ;start of `cp *`
_:
  inc e

  sll e \ rl d
  add a,a \ adc hl,hl
  add a,a \ adc hl,hl
  sbc hl,de
  jr nc,+_
  add hl,de
  dec e
  .db $FE     ;start of `cp *`
_:
  inc e

  sll e \ rl d
  add a,a \ adc hl,hl
  add a,a \ adc hl,hl
  sbc hl,de
  jr nc,+_
  add hl,de
  dec e
  .db $FE     ;start of `cp *`
_:
  inc e

  sll e \ rl d
  add a,a \ adc hl,hl
  add a,a \ adc hl,hl
  sbc hl,de
  jr nc,+_
  add hl,de
  dec e
  .db $FE     ;start of `cp *`
_:
  inc e

;Now we have four more iterations
;The first two are no problem
  ld a,ixl
  sll e \ rl d
  add a,a \ adc hl,hl
  add a,a \ adc hl,hl
  sbc hl,de
  jr nc,+_
  add hl,de
  dec e
  .db $FE     ;start of `cp *`
_:
  inc e

  sll e \ rl d
  add a,a \ adc hl,hl
  add a,a \ adc hl,hl
  sbc hl,de
  jr nc,+_
  add hl,de
  dec e
  .db $FE     ;start of `cp *`
_:
  inc e

sqrt32_iter15:
;On the next iteration, HL might temporarily overflow by 1 bit
  sll e \ rl d      ;sla e \ rl d \ inc e
  add a,a
  adc hl,hl
  add a,a
  adc hl,hl       ;This might overflow!
  jr c,sqrt32_iter15_br0
;
  sbc hl,de
  jr nc,+_
  add hl,de
  dec e
  jr sqrt32_iter16
sqrt32_iter15_br0:
  or a
  sbc hl,de
_:
  inc e

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
