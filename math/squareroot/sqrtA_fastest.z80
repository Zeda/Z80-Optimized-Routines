;Written by Zeda

sqrtA:
;Input: A
;Output: D is the squareroot, A is the remainder (input-D^2)
;Destroys: E
;speed: 118+{0,6}+{0,7}+{0,7}+{0,3}
;min: 118cc
;max: 141cc
;avg: 129.5cc
;38 bytes
  ld de,5040h       ; 10
  sub e             ; 4
  jr nc,sqrtA_skip1 ;\
  add a,e           ; | branch 1: 12cc
  ld d,10h          ; | branch 2: 18cc
sqrtA_skip1:        ;/

; ----------
  cp d              ; 4
  jr c,sqrtA_skip2  ;\
  sub d             ; | branch 1: 12cc
  set 5,d           ; | branch 2: 19cc
sqrtA_skip2:        ;/

; ----------
  res 4,d           ; 8
  srl d             ; 8
  set 2,d           ; 8
  cp d              ; 4
  jr c,sqrtA_skip3  ;\
  sub d             ; | branch 1: 12cc
  set 3,d           ; | branch 2: 19cc
sqrtA_skip3:        ;/
  srl d             ; 8

; ----------
  inc a             ; 4
  sub d             ; 4
  jr nc,sqrtA_skip4 ;\
  dec d             ; | branch 1: 12cc
  add a,d           ; | branch 2: 15cc
sqrtA_skip4:        ;/
  srl d             ; 8
  ret               ; 10
