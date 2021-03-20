; This smaller ariant of the im2 interrupt setup is a little slower (~500cc),
; but this is rarely (if ever) a time-critical piece of code.
;
; It sets up the 257-byte interrut vector at im2table. Note that im2table needs
; to be a multiple of 256, for example, 0x8800 is 0x88*256. In that example, the
; the im2table is filled with 0x89. If im2table == 0x9000, then it would be
; filled ith 0x91, and in general, (im2table/256)+1.

setupim2:
  di
  ld    hl,im2table    ; multiple of 256 which means L = 0
  ld    a,h
  ld    i,a
  im    2
  inc   a
loop:
  ld    (hl),a
  inc   l
  jr    nz,loop
  inc   h
  ld    (hl),a
  ld    l,a

  ; HL points to where the interrupt handler should be, so store whatever needs
  ; to be there. For example, if your interrupt is my_interrupt, you could store
  ; a `jp my_interrupt` command at HL:

  ; ld (hl),$c3
  ; inc l
  ; ld (hl),my_interrupt & $ff
  ; inc l
  ; ld (hl),my_interrupt >> 8


  ei
  ret
