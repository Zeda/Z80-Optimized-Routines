#ifndef included_itoa_16
#define included_itoa_16
#include conversion/u16toa_destructive.z80


; A related routine can be found at conversion/itoa_16.z80 which preserves
; registers.

;written by Zeda
;Converts a 16-bit signed integer to an ASCII string.
;Note that this version destroys registers.

#ifndef TOK_NEG
#define TOK_NEG '-'
#endif

i16toa:
;Input:
;   DE is the number to convert
;   HL points to where to write the ASCII string (up to 7 bytes needed).
;Output:
;   HL points to the null-terminated ASCII string
;      NOTE: This isn't necessarily the same as the input HL.
;Destroys:
;   DE, BC, AF
  ld a,d
  add a,a
  jp nc,u16toa
  xor a
  sub e
  ld e,a
  sbc a,a
  sub d
  ld d,a
  inc hl  ; make space for a negative sign
  call u16toa
  dec hl
  ld (hl),TOK_NEG
  ret
#endif
