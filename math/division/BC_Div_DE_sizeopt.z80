BC_Div_DE:
;BC/DE ==> BC, remainder in HL
;min: 1166cc
;max: 1310cc
;avg: 1238cc
;22 bytes
  ld hl,0
  ld a,b
  ld b,16

div_loop:
  ;shift the bits from BC into HL
  sla c \ rla
  adc hl,hl
  sbc hl,de
  jr nc,div_inc_acc
  add hl,de
  .db $FE     ;this begins the instruction `cp *`, so it eats the next byte.
div_inc_acc:
  inc c

div_loop_done:
  djnz div_loop
  ld b,a
  ret
