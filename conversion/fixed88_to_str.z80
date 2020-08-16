#ifndef included_fixed88_to_str
#define included_fixed88_to_str

#include "subroutines/itoa_8.z80"


;Written by Zeda.
;This converts a fixed-point number to a string.
;It displays up to 3 digits after the decimal.

fixed88_to_str:
;Inputs:
;   D.E is the fixed-point number
;   HL points to where the string gets output.
;      Needs at most 9 bytes.
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

;Our adjusted number is in A.E
;Now we can print the integer part
  call itoa_8

;Check if we need to print the fractional part
  xor a
  cp e
  jr z,fixed88_to_str_end

;We need to write the fractional part, so seek the end of the string
;Search for the null byte. A is already 0
  cpir

;Write a decimal
  dec hl
  ld (hl),'.'

  ld b,3
_:
;Multiply E by 10, converting overflow to an ASCII digit
  call fixed88_to_str_e_times_10
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

fixed88_to_str_end:
;restore HL
  pop hl
  ret

fixed88_to_str_e_times_10:
  ld a,e
  ld d,0
  add a,a \ rl d
  add a,a \ rl d
  add a,e \ jr nc,$+3 \ inc d
  add a,a
  ld e,a
  ld a,d
  rla
  add a,'0'
  ret
#endif
