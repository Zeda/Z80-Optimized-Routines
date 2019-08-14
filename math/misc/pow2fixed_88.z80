pow2:
;Inputs:
;     HL is the 8.8 fixed point number 'x' for 2^x
;Outputs:
;     DEHL is the 24.8 fixed point result. If there was overflow exceeding 2^24, then this value is set to the max.
     ld a,l
     or a
     push hl     ;save H for later, H is the integer part of the power
     ld hl,1
     jr z,integerpow
     scf      ;set the carry flag so that a bit is rotated into a. This will act as our counter.
;wait until we come across the lowest bit. Also note that we
     rra
     jr nc,$-1
     ld hl,2*256
powloop:
     push af
     call FPSqrtHL    ;returns in HL
     pop af
     srl a
     jr z,integerpow
     jr nc,powloop
     add hl,hl
     jp powloop
integerpow:
     pop bc
;Now b is the integer part for 2^x that we need to multiply HL by.
     ld de,0
     ld a,b
     or a
     ret z

     add hl,hl
     rl e \ rl d \ jr c,wayoverflow
     djnz $-7
     ret
wayoverflow:
     ld hl,-1
     ld d,h
     ld e,l
     ret
