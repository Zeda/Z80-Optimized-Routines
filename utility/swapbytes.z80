swapbytes:
;Swaps BC bytes pointed to by HL and DE
;Inputs:
;     HL points to a spot in memory
;     DE points to a spot in memory
;     BC number of bytes to swap
;Outputs:
;     A is 0
;     BC is 0
;     HL is incremented BC times
;     DE is incremented BC times
;
  ld a,(de)
  ldi
  dec hl
  ld (hl),a
  inc hl
  jp pe,swapbytes
  ret
