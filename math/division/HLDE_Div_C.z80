HLDE_Div_C:
;Input: HLDE is numerator, C<129 is the divisor.
;Output: HLDE is quotient, A is remainder, C is negated
;1021+4{0,15}
;min: 1021cc
;max: 1081cc
;min: 1051cc
;87 bytes
  xor a
  sub c
  ld c,a
HLDE_Div_negC:
;Note: -C<129
;1009+4{0,15}
;min: 1009cc
;max: 1069cc
;min: 1039cc
;84 bytes
  xor a
  call +_
  ld b,h

  ld h,l
  call +_
  ld l,h

  ld h,d
  call +_
  ld d,h

  ld h,e
  call +_
  ld e,h

  ld h,b
  rl e
  rl d
  adc hl,hl
  ret

_:
;216+7{0,1}+{0,8}
;min: 216cc
;max: 231cc
;avg: 224.5cc
  rl h \ rla  \ add a,c \ jr c,$+3 \ sub c
  rl h \ rla  \ add a,c \ jr c,$+3 \ sub c
  rl h \ rla  \ add a,c \ jr c,$+3 \ sub c
  rl h \ rla  \ add a,c \ jr c,$+3 \ sub c
  rl h \ rla  \ add a,c \ jr c,$+3 \ sub c
  rl h \ rla  \ add a,c \ jr c,$+3 \ sub c
  rl h \ rla  \ add a,c \ jr c,$+3 \ sub c
  rl h \ rla  \ add a,c \ ret c \ sub c
  ret
