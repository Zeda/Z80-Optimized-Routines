#ifndef included_uitoa_8
#define included_uitoa_8

;Written by Zeda
;Converts an 8-bit unsigned integer to a string

uitoa_8:
;Input:
;   A is a signed integer
;   HL points to where the null-terminated ASCII string is stored (needs at most 5 bytes)
;Output:
;   The number is converted to a null-terminated string at HL
;Destroys:
;   Up to four bytes at HL
;   All registers preserved.
;on 0 to 9:     238              D=0
;on 10 to 99:   244+20D          D=0 to 9
;on 100 to 255: 257+2{0,6}+20D   D=0 to 5
;min: 238cc
;max: 424cc
;avg: 317.453125cc = 81268/256 = (238*10 + 334*90+313*156)/256
;52 bytes

  push hl
  push de
  push bc
  push af
;A is on [0,255]
;calculate 100s place, plus 1 for a future calculation
  ld b,'0'
  cp 100 \ jr c,$+5 \ sub 100 \ inc b
  cp 100 \ jr c,$+5 \ sub 100 \ inc b

;calculate 10s place digit, +1 for future calculation
  ld de,$0A2F
  inc e \ sub d \ jr nc,$-2
  ld c,a

;Digits are now in D, C, A
; strip leading zeros!
  ld a,'0'
  cp b \ jr z,$+5 \ ld (hl),b \ inc hl \ .db $FE  ; start of `cp *` to skip the next byte, turns into `cp $BB` which will always return nz and nc
  cp e \ jr z,$+4 \ ld (hl),e \ inc hl
  add a,c
  add a,d
  ld (hl),a
  inc hl
  ld (hl),0

  pop af
  pop bc
  pop de
  pop hl
  ret

#endif
