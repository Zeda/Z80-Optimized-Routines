xsp32:
;Inputs: (seed1), (seed2), and (seed3) are 16-bit seeds. (seed1) and (seed2) can't both be 0.
;Outputs: HL is the pseudorandom number
;Destroys: A,DE,BC
;cycle: 281,474,976,645,120
;It would take about 185 years at 15MHz to repeat
;min: 258cc (236cc if using SMC)
;max: 288cc (266cc if using SMC)
;avg: 273cc (251cc if using SMC)
;63 bytes (62 bytes if using SMC)
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
  ex de,hl

#ifdef SMC
seed3 = $+1
  ld hl,33333
#else
  ld hl,(seed3)
#endif

  inc hl
  inc h
  ld (seed3),hl
  add hl,de
  ret
