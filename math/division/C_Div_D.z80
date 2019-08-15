C_Div_D:
;Inputs:
;     C is the numerator
;     D is the denominator
;Outputs:
;     A is the remainder
;     B is 0
;     C is the result of C/D
;     D,E,H,L are not changed
;
  ld b,8
  xor a
C_Div_D_loop:
  sla c
  rla
  cp d
  jr c,+_
  inc c
  sub d
_:
  djnz C_Div_D_loop
  ret
