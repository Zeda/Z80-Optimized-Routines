;This is a routine to set up an IM 2 interrupt
;This example sets the vector table at 0x9900 through 0x9A00 and a jump to the actual routine at 0x9A9A
;Created by calc84maniac
setupim2:
  di
  ld a,$99
  ld bc,$0100
  ld h,a
  ld d,a
  ld l,c
  ld e,b
  ld i,a
  inc a
  ld (hl),a
  ldir
  ld l,a
  ld (hl),$c3
  inc l
  ld (hl),intvec & $ff
  inc l
  ld (hl),intvec >> 8
  im 2
  ei
  ret
