;I have no idea what to call this.
;It was created by calc84maniac

inflateA:
;in: a = ABCDEFGH
;out: hl= AABBCCDDEEFFGGHH
  rrca
  rra
  rra
  ld l,a
  rra
  sra l
  rla
  rr l
  sra l
  rra
  rr l
  sra l

  rrca
  rra
  rra
  ld h,a
  rra
  sra h
  rla
  rr h
  sra h
  rra
  rr h
  sra h
  ret
