#ifndef included_fixed_4_12_to_str
#define included_fixed_4_12_to_str

;Written by Zeda, free to use.
;This converts a 4.12 fixed-point number to a string.
;It displays up to 4 digits after the decimal.

fixed_4_12_to_str:
;Inputs:
;   D.E is the fixed-point number
;   HL points to where the string gets output.
;      Needs at most 8 bytes.
;Outputs:
;   HL is preserved
;Destroys:
;   AF,DE,BC

;First check if the input is negative.
;If so, write a negative sign and negate
  push hl
  ld a,d
  or a
  jp p,+_
  ld (hl),$1A      ;negative sign on TI-OS
  inc hl
  xor a
  sub e
  ld e,a
  sbc a,a
  sub d
_:

;Get the first digit (between 0 and 7)
  ld d,a
  rrca
  rrca
  rrca
  rrca
  and 15
  add a,'0'
  ld (hl),a
  inc hl

; Check if we have a fractional part
  ld a,d
  and $0F
  ld d,a
  or e
  jr nz,$+5
  ld (hl),a
  pop hl
  ret

;Write a decimal
  ld (hl),'.'

; DE is the 12 fractional bits. Shift left 4 and add 3 (for rouding)
  ex de,hl
  add hl,hl
  add hl,hl
  add hl,hl
  inc l
  add hl,hl
  inc l
  ex de,hl


  ld b,4
_:
;Multiply DE by 10, converting overflow to an ASCII digit
  call fixed_4_12_to_str_de_times_10
  inc hl
  ld (hl),a
  djnz -_

;Strip the ending zeros
  ld a,'0'
_:
  cp (hl)
  dec hl
  jr z,-_

;write a null byte
  inc hl
  inc hl
  ld (hl),0

;restore HL
  pop hl
  ret

fixed_4_12_to_str_de_times_10:
  push hl
  xor a
  ld h,d
  ld l,e
  add hl,hl \ rla
  add hl,hl \ rla
  add hl,de \ adc a,$18     ; half of '0'
  add hl,hl \ rla
  ex de,hl
  pop hl
  ret

#endif
