rand5:
;Returns A on [0,4]
;Destroys: All
;Notes:
; This is a non-standard approach to generating random integers on [0,4].
; If you have a truly random number generator that generates bits (0 or 1)
; with equal probability, then standard approaches will still cause a slight
; bias. ("Standard": "rand mod 5" or int(5*rand)). For example, suppose we
; generate a 4-bit number. Then "rand mod 5" will cause 0 to be chosen
; 4/16 times, while 1, 2, 3, and 4 will be chosen 3/16 times (on average).
; A similar problem exists with int(5*rand). One way to mitigate this issue
; is just generating infintely many bits, but apparently that is impractical,
; so I came up with a compromise.
;
; My approach basically looks at the binary expansion of 1/5, 2/5, 3/5, and 4/5.
;   1/5 = .0011001100110011...
;   2/5 = .0110011001100110...
;   3/5 = .1001100110011001...
;   4/5 = .1100110011001100...
;
; So if I generate random bits and I get .001100, then a 0, then I know
; that no matter what all of the rest of the bits are, the number is less than
; 1/5, and so int(5*rand) is 0.
;
; By applying similar logic to the rest of the values, I can guarantee a uniform
; distribution on [0,4]. But there are four cases where this process might
; continue forever, specifically the cases that are like ...00110011...., but
; lucky for us, this happens 4/inf= 0% of the time. In fact, on average it
; takes 3 to 4 bits before the algorithm can assert which value to return.
;
; The one caveat is that on the Z80, we generally don't have truly random
; numbers :| On the otherhand, it is easy enough to generate pseudo-random
; bits with equal probability :)

  call rand
  ld a,h
  and $C0
  push af    ;save the original value
  ld c,a
rand5_start:
  push bc
  call rand
  pop bc
  ld b,15    ;I set this to 15 because I like to guarantee a bit is available for rand10.
rand5_loop:
  ld a,h
  xor c
  jp p,rand5_end
  add hl,hl
  sla c
  jr c,$+4
  set 6,c
  djnz rand5_loop
  jr rand5_start

rand5_end:
  pop af
  rlca
  rlca
  sla h
  adc a,0
  ret
