;Converts an ASCII string to an unsigned 16-bit integer
;Quits when it reaches a non-decimal digit

string_to_uint16:
atoui_16:
;Input:
;     DE points to the string
;Outputs:
;     HL is the result
;     A is the 8-bit value of the number
;     DE points to the byte after the number
;Destroys:
;     BC
;       if the string is non-empty, BC is HL/10
;Size:  24 bytes
;Speed: 42+d(104+{0,9})
;       d is the number of digits in the number
;       max is 640 cycles for a 5 digit number
;Assuming no leading zeros:
;1 digit:  146cc
;2 digit:  250cc
;3 digit:  354cc or 363cc (avg: 354.126cc)
;4 digit:  458cc or 467cc (avg: 458.27cc)
;5 digit:  562cc or 571cc or 580cc (avg: 562.4104cc)
;avg: 544.81158447265625cc (544+13297/16384)
;===============================================================
  ld hl,0
_:
  ld a,(de)
  sub 30h
  cp 10
  ret nc
  inc de
  ld b,h
  ld c,l
  add hl,hl
  add hl,hl
  add hl,bc
  add hl,hl
  add a,l
  ld l,a
  jr nc,-_
  inc h
  jp -_
