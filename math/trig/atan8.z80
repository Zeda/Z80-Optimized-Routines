atan8:
;computes 256*atan(A/256)->A
;56 bytes including the LUT
;min: 246cc
;max: 271cc
;avg: 258.5cc
  rlca
  rlca
  rlca
  ld d,a
  and 7
  ld hl,atan8LUT
  add a,l
  ld l,a
#if (atan8LUT&255)>248    ;this section not included in size/speed totals
  jr nc,$+3               ;can add three bytes, 12cc to max, 11cc to min, and 11.5cc to avg
  inc h
#endif
  ld c,(hl)
  inc hl
  ld a,(hl)
  sub c
  ld e,0
  ex de,hl
  ld d,l
  ld e,a
  sla h \ jr nc,$+3 \ ld l,e
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl \ jr nc,$+3 \ add hl,de
  add hl,hl
  add hl,hl
  add hl,hl
;  add hl,hl    ;used in rounding...
  ld a,h
;  rra          ;but doesn't seem to improve the error
  adc a,c
  ret
atan8LUT:
  .db 0,32,63,92,119,143,165,184,201