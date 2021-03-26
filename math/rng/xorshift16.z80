;You may use this routine, just be sure to credit John Metcalf!
;Written by John Metcalf
;   http://www.retroprogramming.com/2017/07/xorshift-pseudorandom-numbers-in-z80.html
;
; Annotated by Zeda Thomas, fixed typo (86 cycles==> 82 cycles)

;Note: uses SMC

; 16-bit xorshift pseudorandom number generator
; 20 bytes, 82 cycles (excluding ret)

; returns   hl = pseudorandom number
; corrupts   a

xrnd:
  ld hl,1         ; Init the seed, must not be 0
  ld a,h          ;\
  rra             ; | Get the top bits of xs<<7 and xor with the top byte of HL
  ld a,l          ; |        abcdefgh ijklmnop
  rra             ; |       ^hijklmno 00000000
  xor h           ; | Note that we still need to xor the 'p' with the top byte of l
  ld h,a          ;/
  ld a,l          ;\
  rra             ; | we get 'p' in the carry flag, now shift that in when we do xs>>9
  ld a,h          ; |        abcdefgh ijklmnop   (new value)
  rra             ; |       ^00000000 pabcdefg
  xor l           ; | the 'p' is leftover from the first step, so now Step 1 and 2 are done
  ld l,a          ;/
  xor h           ;\ Finally, xor the bottom byte with the top byte for step 3
  ld h,a          ;/
  ld (xrnd+1),hl  ; write back the new value as the next seed
  ret
