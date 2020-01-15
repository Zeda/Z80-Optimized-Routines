;Made by Zeda Thomas, use it for whatever, and please optimize this!
;Slight Warning: This passed a handful of tests, but if you find a bug,
;please report it. I still actively maintain these (as of January 2020).

div_32_32:
;Inputs:
;   HLIX/BCDE
;Outputs:
;   HLIX is the quotient
;   BCDE is the remainder
;RAM:
;   uses 8 bytes of RAM:
;     4 bytes at temp32_0
;     4 bytes at temp32_1
;
;min: 5240cc
;max: 6264cc
;avg: 5752cc
;113 bytes

; Back up HLIX
  ld (temp32_0),ix
  ld (temp32_0+2),hl


;negate BCDE
  xor a
  ld l,a \ sbc a,e \ ld e,a
  ld a,l \ sbc a,d \ ld d,a
  ld a,l \ sbc a,c \ ld c,a
  ld a,l \ sbc a,b \ ld b,a

  ld a,h
;set HLIX to 0
  ld h,l
  ld ix,0
  call div_32_by_32_sub
  ld (temp32_0+3),a

  ld a,(temp32_0+2)
  call div_32_by_32_sub
  ld (temp32_0+2),a

  ld a,(temp32_0+1)
  call div_32_by_32_sub
  ld (temp32_0+1),a

  ld a,(temp32_0+0)
  call div_32_by_32_sub
  ld (temp32_0),a

  push ix
  pop de
  ld b,h
  ld c,l
  ld ix,(temp32_0)
  ld hl,(temp32_0+2)
  ret



div_32_by_32_sub:
;min: 1223cc
;max: 1479cc
;avg: 1351cc

  call +_
_:
  call +_
_:
  call +_
_:
;min: 138cc
;max: 170cc
;avg: 154cc
;HLIX*2
  add ix,ix
  adc hl,hl

;rotate in the bit
  add a,a
  jr nc,+_
  inc ix
_:

;save HLIX in case we need to restore
  ld (temp32_1),ix
  ld (temp32_1+2),hl

;check if HLIX>=-BCDE
;     ==> HLIX+BCDE >= 0
  add ix,de
  adc hl,bc
  jr c,+_

;we need to restore
  ld ix,(temp32_1)
  ld hl,(temp32_1+2)
  ret
_:
  inc a
  ret
