;written by calc84maniac
;comment from calc84maniac:
;   To clarify why I did a cpl/scf/adc instead of a cpl/inc/add or neg/add,
;   is that it handles the case of A=0 properly. Typically, SUB N and
;   ADD A,-N give opposite carry outputs, but SUB 0 and ADD A,-0 both reset the
;   carry flag. On the other hand, SCF \ ADC A,255 will set the carry flag like
;   we want it to.

;NOTE: This is an in-line routine-- there is no RET
  cpl
  scf
  adc a,c
  ld c,a
  jr c,$+3
  dec b


; Here is a callable routine:
  cpl
  scf
  adc a,c
  ld c,a
  ret c
  dec b
  ret
