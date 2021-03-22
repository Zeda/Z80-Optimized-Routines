stringlength:
;Inputs:
;   HL points to the null-terminated string
;Outputs:
;   BC is the length of the string
;   HL points to the byte after the null-byte
;Destroys:
;   A
;speed: 41+21n
;12 bytes
  xor a
  ld c,a
  ld b,a
  cpir
  scf       ;comment this if the NULL byte should be counted
  sbc a,c
  ld c,a
  sbc a,a
  sub b
  ld b,a
  ret
