HL_Div_3:
;Input: HL
;Output: HL is the input divided by 3
;Destroys: B,C,E,A
;217cc

;increment HL, putting overflow in A
  ld bc,1
  ld a,b
  add hl,bc
  adc a,b

;We want a difference of a factor of 2 shifts
  ld b,h
  ld c,l
  ld e,a
  add hl,hl \ rla
  add hl,hl \ rla
  add hl,bc \ adc a,e

;We want a difference of a factor of 4 shifts
  ld b,h
  ld c,l
  ld e,a
  add hl,hl \ rla
  add hl,hl \ rla
  add hl,hl \ rla
  add hl,hl \ rla
  add hl,bc \ adc a,e

  ld b,a
  ld c,h
  add hl,bc
  adc a,0
  ld l,h
  ld h,a
;now HL is our result

  ret
