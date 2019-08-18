;Adapted from Axe

sqrtHL:
;Input: HL
;Output: D is the square root, cH is the remainder (c being the c flag), A is 0, B is 0, L is 0
;speed: 758+8{0,6}
;min: 758cc
;max: 806cc
;avg: 782cc
;26 bytes
p_Sqrt:
	ld	a,l
	ld	l,h
	ld	de,$0040
	ld	h,d
	ld	b,8
	or	a
__SqrtLoop:
	sbc	hl,de
	jr	nc,__SqrtSkip
	add	hl,de
__SqrtSkip:
	ccf
	rl	d
	add a,a
	adc	hl,hl
	add a,a
	adc	hl,hl
	djnz	__SqrtLoop
	ret
