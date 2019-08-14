;Call this from a routine.
;This disables interrupts, but sets up a return routine that restores interrupts
;to the state they were in previously. Very useful if an environment may need
;interrupts enabled, but your routine needs them disabled.

diRestore:
    ex (sp),hl
    push hl
    push af
    ld hl,restoreei
    ld a,r
    jp pe,+_
    dec hl
    dec hl
_:
    di
    inc sp
    inc sp
    inc sp
    inc sp
    ex (sp),hl
    dec sp
    dec sp
    dec sp
    dec sp
    pop af
    ret
restoredi:
    di
    ret
restoreei:
    ei
    ret
