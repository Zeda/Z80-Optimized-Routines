lehmer:
;Input:
;  (seed) has the seed value of the RNG
;Output:
;  (seed) is updated, HL is the result
;Destroys:
;  A,DE,BC
;Timing:
;  if seed>0        231cc or 232cc, condition dependent
;  if seed=0        91cc
;  if SMC defined   subtract 6cc
;Size: 44 bytes
;Notes:
;    Uses the Lehmer RNG used by the Sinclair ZX81
;    75x mod 65537 -> x
#ifndef SMC
    ld hl,(seed)
#else
seed = $+1
    ld hl,0
#endif
;multiply by 75
    ld c,l
    ld b,h
    xor a
    adc hl,hl \ jr z,special \ ld d,a \ rla
    add hl,hl \ rla
    add hl,hl \ rla \ add hl,bc \ adc a,d
    add hl,hl \ rla
    add hl,hl \ rla \ add hl,bc \ adc a,d
    add hl,hl \ rla \ add hl,bc
;modulo 65537, see note below on how this works
    ld e,a
    sbc hl,de       ;No need to reset the c flag since it is already
    jr nc,$+3
    inc hl
    ld (seed),hl
    ret
special:
;In the case that HL=0, this should be interpreted as 65536 = -1 mod 65537, so return -75 mod 65537 = -74 mod 65536 in HL
    ld hl,-74
    ld (seed),hl
    ret

;mod by 2^16 + 1 (a prime)
;current form is A*2^16+HL
;need:
;  (A*2^16+HL) mod (2^16+1)
;add 0 as +1-1
;  (A*(2^16+1-1)+HL) mod (2^16+1)
;distribute
;  (A*(2^16+1)-A+HL) mod (2^16+1)
;A*(2^16+1) mod 2^16+1 = 0, so remove
;  (-A+HL) mod (2^16+1)
;Oh hey, that's easy! :P
;I use this trick everywhere, you should, too.
