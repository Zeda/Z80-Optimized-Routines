lfsr64:
;;Output: A is an 8-bit pseudo-random number.
    ld hl,seed
    sla (hl) \ inc hl
    rl (hl) \ inc hl
    rl (hl) \ inc hl
    rl (hl) \ inc hl
    rl (hl) \ inc hl
    rl (hl) \ inc hl
    rl (hl) \ inc hl
    rl (hl)
    ret nc
    ld a,(seed)
    xor %000011011
    ld (seed),a
    ret

