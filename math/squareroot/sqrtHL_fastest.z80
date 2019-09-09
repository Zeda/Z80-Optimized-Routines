;written by Zeda
sqrtHL:
;returns A as the sqrt, HL as the remainder, D = 0
;min: 352cc
;max: 391cc
;avg: 371.5cc


  ld de,05040h  ; 10
  ld a,h        ; 4
  sub e         ; 4
  jr nc,sq7     ;\
  add a,e       ; | branch 1: 12cc
  ld d,16       ; | branch 2: 18cc
sq7:            ;/

; ----------

  cp d          ; 4
  jr c,sq6      ;\
  sub d         ; | branch 1: 12cc
  set 5,d       ; | branch 2: 19cc
sq6:            ;/

; ----------
  res 4,d       ; 8
  srl d         ; 8
  set 2,d       ; 8
  cp d          ; 4
  jr c,sq5      ;\
  sub d         ; | branch 1: 12cc
  set 3,d       ; | branch 2: 19cc
sq5:            ;/
  srl d         ; 8

; ----------

  inc a         ; 4
  sub d         ; 4
  jr nc,sq4     ;\
  dec d         ; | branch 1: 12cc
  add a,d       ; | branch 2: 19cc
  dec d         ; | <-- this resets the low bit of D, so `srl d` resets carry.
sq4:            ;/
  srl d         ; 8
  ld h,a        ; 4

; ----------

  ld a,e        ; 4
  sbc hl,de     ; 15
  jr nc,sq3     ;\
  add hl,de     ; | 12cc or 18cc
sq3:            ;/
  ccf           ; 4
  rra           ; 4
  srl d         ; 8
  rra           ; 4

; ----------

  ld e,a        ; 4
  sbc hl,de     ; 15
  jr c,sq2      ;\
  or 20h        ; | branch 1: 23cc
  db 254        ; |   <-- start of `cp *` which is 7cc to skip the next byte.
sq2:            ; | branch 2: 21cc
  add hl,de     ;/

  xor 18h       ; 7
  srl d         ; 8
  rra           ; 4

; ----------

  ld e,a        ; 4
  sbc hl,de     ; 15
  jr c,sq1      ;\
  or 8          ; | branch 1: 23cc
  db 254        ; |   <-- start of `cp *` which is 7cc to skip the next byte.
sq1:            ; | branch 2: 21cc
  add hl,de     ;/

  xor 6         ; 7
  srl d         ; 8
  rra           ; 4

; ----------

  ld e,a        ; 4
  sbc hl,de     ; 15
  jr nc,+_      ;    \
  add hl,de     ; 15  |
  srl d         ; 8   |
  rra           ; 4   | branch 1: 38cc
  ret           ; 10  | branch 2: 40cc
_:              ;     |
  inc a         ; 4   |
  srl d         ; 8   |
  rra           ; 4   |
  ret           ; 10 /
