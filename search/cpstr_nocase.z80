cpstr_nocase:
;Compare two strings at HL and DE, with lowercase being equal to uppercase
;returns z if they are equal
;returns c if HL points to the smaller string
;returns nc if HL is the bigger (or equal) string.
;destroys A,C,DE,HL
;preserves B
;26 bytes

  ld a,(de)
  call toUpper
  ld c,a
  ld a,(hl)
  call toUpper
  cp c
  inc de
  inc hl
  ret nz
  or a
  jr nz,cpstr
  ret

toUpper:
;A is the char.
;If A is a lowercase letter, this sets it to the matching uppercase
;18cc or 30cc or 41cc
;avg: 26.75cc
  cp 'a'
  ret c
  cp 'z'+1
  ret nc
  sub 'a'-'A'
  ret
