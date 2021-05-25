#ifndef included_u16toa
#define included_u16toa

; A related routine can be found at conversion/utoa_16.z80 which preserves
; registers.

;written by Zeda
;Converts a 16-bit unsigned integer to an ASCII string.
;Note that this version destroys registers.

u16toa:
;Input:
;   DE is the number to convert
;   HL points to where to write the ASCII string (up to 6 bytes needed).
;Output:
;   HL points to the null-terminated ASCII string
;      NOTE: This isn't necessarily the same as the input HL.
;Destroys:
;   BC, DE, AF
  ex de,hl

; First digit
  ld bc,-10000
  ld a,'0'-1
  inc a     ;\
  add hl,bc ; | Loop
  jr c,$-2  ;/
  ld (de),a
  inc de

; Second digit
  ld bc,1000
  ld a,'9'+1
  dec a     ;\
  add hl,bc ; | Loop
  jr nc,$-2 ;/
  ld (de),a
  inc de

; Third digit
  ld bc,-100
  ld a,'0'-1
  inc a     ;\
  add hl,bc ; | Loop
  jr c,$-2  ;/
  ld (de),a
  inc de

; Fourth digit, remainder is fifth digit
  ld a,l
  ld h,'9'+1
  dec h     ;\
  add a,10  ; | Loop
  jr nc,$-3 ;/
  ex de,hl
  ld (hl),d
  inc hl
  add a,'0'
  ld (hl),a
  inc hl
  ld (hl),0

;Now strip the leading zeros
  ld c,-6
  add hl,bc

  ld a,'0'
  inc hl    ;\
  cp (hl)   ; | Loop
  jr z,$-2  ;/

;Make sure that the string is non-empty!
  xor a
  cp (hl)
  ret z
  dec hl
  ret
#endif
