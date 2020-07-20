;This code snippet is 9 bytes and 43cc
;Inputs:
;   HL is the input seed and must be non-zero
;Outputs:
;   A is the 8-bit pseudo-random number
;   HL is the new seed value (will be non-zero)
                  ;opcode cc
    add hl,hl     ; 29    11
    sbc a,a       ; 9F     4
    and %00101101 ; E62D   7
    xor l         ; AD     4
    ld l,a        ; 6F     4
    ld a,r        ; ED5F   9
    add a,h       ; 84     4

;-------------------------------------------------------------------------------
;Technical details:
;   The concept behind this routine is to combine an LFSR (poor RNG) with a
; counter. The counter improves the RNG quality, while also extending the period
; length.
;   For this routine, I took advantage of the Z80's built-in counter, the `r`
; register. This means that we don't need to store the counter anywhere, and it
; is pretty fast to access!
;   Some caveats:
;     * r is a 7-bit counter
;     * r will increment some number of times between runs of the RNG. In most
;       cases, this will be constant, but if it increments an even number each
;       time, then the bottom bit is always the same, weakening the effect of
;       the counter. In the worst case, it increments a multiple of 128 times,
;       effectively making your RNG just as good/bad as the LFSR. Ideally, you
;       want `r` to increment an odd number of times between runs.
;     * In the best case, the bottom 7 bits have 50/50 chance of being 0 or 1.
;       The top bit is 1 with probability 1/2 + 1/(2^17-2) ~ .5000076295
;     * In the event that your main loop waits for user input between calls,
;       then congatulations, you might have a True RNG :)
;-------------------------------------------------------------------------------
