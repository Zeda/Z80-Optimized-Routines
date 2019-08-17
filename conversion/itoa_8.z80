#ifndef included_itoa_8
#define included_itoa_8

;Written by Zeda
;Converts an 8-bit signed integer to a string

itoa_8:
;Input:
;   A is a signed integer
;   HL points to where the null-terminated ASCII string is stored (needs at most 5 bytes)
;Output:
;   The number is converted to a null-terminated string at HL
;Destroys:
;   Up to five bytes at HL
;   All registers preserved.
;on 0 to 9:       252       D=0
;on 10 to 99:     258+20D   D=0 to 9
;on 100 to 127:   277+20D   D=0 to 2
;on -1 to -9:     276       D=0
;on -10 to -99:   282+20D   D=0 to 9
;on -100 to -128: 301+20D   D=0 to 2

;min: 252cc  (+23cc over original)
;max: 462cc  (-49cc over original)
;avg: 343.74609375cc = 87999/256
;54 bytes
  push hl
  push de
  push bc
  push af
  or a
  jp p,itoa_pos
  neg
  ld (hl),$1A  ;start if neg char on TI-OS
  inc hl
itoa_pos:
;A is on [0,128]
;calculate 100s place, plus 1 for a future calculation
  ld b,'0'
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
