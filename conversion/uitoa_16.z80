#ifndef included_uitoa_16
#define included_uitoa_16

;written by Zeda
;Converts a 16-bit unsigned integer to an ASCII string.

uitoa_16:
;Input:
;   DE is the number to convert
;   HL points to where to write the ASCII string (up to 6 bytes needed).
;Output:
;   HL points to the null-terminated ASCII string
;      NOTE: This isn't necessarily the same as the input HL.
  push de
  push bc
  push af
  ex de,hl

  ld bc,-10000
  ld a,'0'-1
  inc a \ add hl,bc \ jr c,$-2
  ld (de),a
  inc de

  ld bc,1000
  ld a,'9'+1
  dec a \ add hl,bc \ jr nc,$-2
  ld (de),a
  inc de

  ld bc,-100
  ld a,'0'-1
  inc a \ add hl,bc \ jr c,$-2
  ld (de),a
  inc de

  ld a,l
  ld h,'9'+1
  dec h \ add a,10 \ jr nc,$-3
  add a,'0'
  ex de,hl
  ld (hl),d
  inc hl
  ld (hl),a
  inc hl
  ld (hl),0

;Now strip the leading zeros
  ld c,-6
  add hl,bc
  ld a,'0'
  inc hl \ cp (hl) \ jr z,$-2

;Make sure that the string is non-empty!
  ld a,(hl)
  or a
  jr nz,+_
  dec hl
_:

  pop af
  pop bc
  pop de
  ret

#endif
