;author: calcmaniac84, I think
;Copy zero terminated string at HL to DE.
strcopy:
 xor a
docopystr:
 cp (hl)
 ldi
 jr nz,docopystr
 ret
