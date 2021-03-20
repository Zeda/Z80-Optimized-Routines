stringlength_8bit:
; Input: HL points to the null-terminated string (less than 256 bytes long)
; Output: A is the length of the string
  xor  a
  ld   c,a
  cpir
  sub  c
;   dec  a  ; comment if the null byte is supposed to be included in the length
  ret
