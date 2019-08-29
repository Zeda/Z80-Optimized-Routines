rand32:
;Tested and passes all CAcert tests
;Uses a very simple 32-bit LCG and 32-bit LFSR
;it has a period of 18,446,744,069,414,584,320
;roughly 18.4 quintillion.
;LFSR taps: 0,2,6,7  = 11000101
;291cc
;Thanks to Runer112 for his help on optimizing the LCG and suggesting to try the much simpler LCG. On their own, the two are terrible, but together they are great.
;58 bytes
seed1_0=$+1
    ld hl,12345
seed1_1=$+1
    ld de,6789
    ld b,h
    ld c,l
    add hl,hl \ rl e \ rl d
    add hl,hl \ rl e \ rl d
    inc l
    add hl,bc
    ld (seed1_0),hl
    ld hl,(seed1_1)
    adc hl,de
    ld (seed1_1),hl
    ex de,hl
;;lfsr
seed2_0=$+1
    ld hl,9876
seed2_1=$+1
    ld bc,54321
    add hl,hl \ rl c \ rl b
    ld (seed2_1),bc
    sbc a,a
    and %11000101
    xor l
    ld l,a
    ld (seed2_0),hl
    ex de,hl
    add hl,bc
    ret
