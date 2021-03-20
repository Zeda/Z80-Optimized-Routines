fastldir:
;copy BC bytes from HL to DE
;
;116 + 16*BC + 10*ceil(BC/16)
;
;If you call this routine, add 17cc as overhead, and it breaks even with LDIR at 34 bytes
;If you jp to this routine, add 10cc as overhead, and break-even is 31 bytes
;
    push hl
    push af
    xor a
    sub c
    and 15               ;change to n-1, n must be a power of 2
    add a,a
    add a,ldirloop&255
    ld l,a
    adc a,ldirloop>>8
    sub l
    ld h,a
    pop af
    ex (sp),hl
    ret

ldirloop:
;n=16, (number of LDI instructions, use qty of 4,8,16,32,64)
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
    ldi
_ldirloop_end:
    ldi
    jp pe,ldirloop
    ret
