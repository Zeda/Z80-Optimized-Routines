BC_Div_DE:
;BC/DE ==> BC, remainder in HL
;NOTE: BC/0 returns 0 as the quotient.
;min: 738cc
;max: 898cc
;avg: 818cc
;144 bytes
  xor a
  ld h,a
  ld l,a
  sub e
  ld e,a
  sbc a,a
  sub d
  ld d,a

  ld a,b
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla
  ld b,a

  ld a,c
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla \ adc hl,hl \ add hl,de \ jr c,$+4 \ sbc hl,de
  rla
  ld c,a

  ret
