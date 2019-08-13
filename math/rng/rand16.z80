;#define smc	;uncomment if you are using SMC
rand16:
;collaboration by Zeda with Runer112
;160cc or 148cc if using SMC
;26 bytes
;cycle: 4,294,901,760 (almost 4.3 billion)
#ifdef smc
seed1=$+1
	ld hl,9999
#else
    ld hl,(seed1)
#endif
    ld b,h
    ld c,l
    add hl,hl
    add hl,hl
    inc l
    add hl,bc
    ld (seed1),hl
#ifdef smc
seed2=$+1
	ld hl,9999
#else
    ld hl,(seed2)
#endif
    add hl,hl
    sbc a,a
    and %00101101
    xor l
    ld l,a
    ld (seed2),hl
    add hl,bc
    ret
