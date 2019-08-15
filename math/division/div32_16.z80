div32_16:
;HLIX/BC -> HLIX remainder DE
;174+4*div32_16_sub8
;min: 2186cc
;max: 2794cc
;avg: 2466cc
;61 bytes
  ex de,hl   ; 4

; Negate BC to allow add instead of sbc
  xor a      ; 4
; Need to set HL to 0 anyways, so save 2cc and a byte
  ld h,a     ; 4
  ld l,a     ; 4
  sub c      ; 4
  ld c,a     ; 4
  sbc a,a    ; 4
  sub b      ; 4
  ld b,a     ; 4


  ld a,d              ; 4
  call div32_16_sub8  ; 17
  rla                 ; 4
  ld d,a              ; 4

  ld a,e              ; 4
  call div32_16_sub8  ; 17
  rla                 ; 4
  ld e,a              ; 4

  ld a,ixh            ; 8
  call div32_16_sub8  ; 17
  rla                 ; 4
  ld ixh,a            ; 8

  ld a,ixl            ; 8
  call div32_16_sub8  ; 17
  rla                 ; 4
  ld ixl,a            ; 8

  ex de,hl   ; 4
  ret        ; 10

div32_16_sub8:
;119+8*div32_16_sub
;min: 503cc
;max: 655cc
;avg: 573cc
  call +_
_:
;17+2(17+2(div32_16_sub)))
  call +_
_:
;17+2(div32_16_sub)
  call div32_16_sub
div32_16_sub:
;48+{8,0+{0,19}}
;min: 48cc
;max: 67cc
;avg: 56.75cc
  rla        ; 4
  adc hl,hl  ; 15
  jr c,+_    ;12/7
  add hl,bc  ; 11
  ret c      ;11/5
  sbc hl,bc  ; 15
  ret        ; 10
_:
  add hl,bc  ; 11
  scf        ; 4
  ret        ; 10
