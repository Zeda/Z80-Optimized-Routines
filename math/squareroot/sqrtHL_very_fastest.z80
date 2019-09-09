; fast 16-bit isqrt by Zeda Thomas
;Feel free to use for whatever :)

sqrtHL:
;Input: HL
;Output: A is the integer square root of HL
;Destroys: HL,DE (D is actually 0)
;min: 343cc
;max: 380cc
;avg: 361.5cc
;88 bytes
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

;This code would restore the square root
;   jr nc,sq0      ;\
;   add hl,de     ; | 12cc or 18cc
; sq0:            ;/

  sbc a,255     ; 7
  srl d         ; 8
  rra           ; 4
  ret           ; 10
