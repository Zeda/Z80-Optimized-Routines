;NOTE: This is a set of in-line routines!


; Input: HL
; Output: BC is the input, HL is 12 times the input
; 6 bytes, 52cc
  ld b,h
  ld c,l
  add hl,hl
  add hl,bc
  add hl,hl
  add hl,hl


;Destroys only register E and F
; Input: HL <= 85,
; 8 bytes, 46cc
   ld e,a
   ld a,l
   add a,a   ; hl*2
   add a,l   ; hl*3
   ld l,a
   ld a,e
   add hl,hl ; hl*6
   add hl,hl ; hl*12


;Destroys only register E and F
; Input: HL <= 85,
; 7 bytes, 55cc
   ld e,l
   add hl,hl ; hl*2
   add hl,de ; hl*3+d*256
   ld h,0    ; hl*3
   add hl,hl ; hl*6
   add hl,hl ; hl*12
