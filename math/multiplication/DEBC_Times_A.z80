DEBC_Times_A:
;Inputs:
;   DEBC is a 32-bit multiplicand
;   A is an 8-bit multiplicand
;Outputs:
;   AHLIX is the 40-bit result
;   carry reset
;   z set if top 8 bits are 0
;   sign flag set as expected
;===============================================================

;503+8{0,41}
;min: 503cc
;max: 831cc
;avg: 667cc
;29 bytes
  ld hl,0
  ld ix,0
  call +_
_:
;231+4{0,41}
  call +_
_:
;107+2{0,41}
  call +_
_:
;45+{0,41}
  add ix,ix
  adc hl,hl
  adc a,a
  ret nc
  add ix,bc
  adc hl,de
  adc a,0
  ret
