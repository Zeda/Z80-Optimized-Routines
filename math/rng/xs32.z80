xs32:
;32-bit xorshift
;seed^=seed<<23
;seed^=seed>>15
;seed^=seed<<17
;min: 209cc (193cc if using SMC)
;max: 239cc (223cc if using SMC)
;avg: 224cc (208cc if using SMC)
;53 bytes (52 bytes if using SMC)
#ifdef SMC
seed1 = $+1
  ld hl,12345
seed2 = $+1
  ld de,6789
#else
  ld hl,(seed1)
  ld de,(seed2)
#endif

;first, XOR it with itself, shifted left 23 bits
;low bit of d needs to be shifted in
  ld a,h
  rra
  ld a,l
  rra
  jr nc,+_
  rl e
  ccf
  rr e
_:
  xor d
  ld d,a

;XOR it with itself, shifted right 15 bits
  ld a,h
  rla
  ld a,e
  rla
  xor l
  ld l,a

  ld a,e
  rla
  ld a,d
  rla
  jr nc,+_
  rr e
  ccf
  rl e
_:
  xor h
  ld h,a

;XOR it with itself, shifted left 17 bits
;HL<<1
  ld (seed1),hl
  add hl,hl
  ld a,h
  xor d
  ld h,a

  ld a,l
  xor e
  ld l,a
  ld (seed2),hl
  ret
