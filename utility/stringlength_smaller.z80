;This version returns the string length without the null byte
stringlength:
; Input: HL points to the null-terminated string
; Output: HL is the length of the string
;speed: 40cc+21n (+4cc if `scf` is uncommented)
;10 bytes (+1 byte if `scf` is uncommented)
  xor a
  ld d,h
  ld e,l
  ld b,a
  ld c,a
  cpir
  ;scf      ; comment if the null byte is supposed to be included in the length
  sbc hl,de
  ret
