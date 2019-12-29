cpstr_nocase:
;Compare two strings at HL and DE, with lowercase being equal to uppercase
;returns z if they are equal
;returns c if HL points to the smaller string
;returns nc if HL is the bigger (or equal) string.
;destroys A,C,DE,HL
;preserves B
;31 bytes.
  ld a,(de)
  cp 'a'
  jr c,+_
  cp 'z'+1
  jr nc,+_
  sub 'a'-'A'
_:
  ld c,a

  ld a,(hl)
  cp 'a'
  jr c,+_
  cp 'z'+1
  jr nc,+_
  sub 'a'-'A'
_:

  cp c
  inc de
  inc hl
  ret nz
  or a
  jr nz,cpstr
  ret
