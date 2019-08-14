DE_Times_A:
;Inputs:
;     DE and A are factors
;Outputs:
;     A is not changed
;     B is 0
;     C is not changed
;     DE is not changed
;     HL is the product
;Time:
;     342+6x
;13 bytes
  ld b,8      ;7           7
  ld hl,0     ;10         10
_:
  add hl,hl   ;11*8       88
  rlca        ;4*8        32
  jr nc,$+3   ;(12|18)*8  96+6x
  add hl,de   ;--         --
  djnz -_     ;13*7+8     99
  ret         ;10         10
