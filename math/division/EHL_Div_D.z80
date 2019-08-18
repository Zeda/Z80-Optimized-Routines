EHL_Div_D:
;1360+24({0,3+{0,3}})
;min: 1360cc
;max: 1504cc
;avg: 1414cc
;17 bytes
  xor a
  ld b,24
_:
  add hl,hl
  rl e
  rla
  jr c,$+5    ;if D is guaranteed <129, can omit this
  cp d
  jr c,$+4
  sub d
  inc l
  djnz -_
  ret
