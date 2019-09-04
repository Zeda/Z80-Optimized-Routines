LFSR:
;13 bytes
;72cc (66cc if using SMC)
;period is 65535
#ifdef SMC
seed = $+1
    ld hl,9797
#else
    ld hl,(seed)
#endif
    add hl,hl
    sbc a,a
    and %00101101
    xor l
    ld l,a
    ld (seed),hl
    ret
