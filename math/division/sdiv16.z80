;Adapted from Axe

p_SDiv:
	ld	a,h
	xor	d
	push	af
	xor	d
	jp	p,__SDivSkip1
	xor	a
	sub	l
	ld	l,a
	sbc	a,a
	sub	h
	ld	h,a
__SDivSkip1:
	bit	7,d
	jr	z,__SDivSkip2
	xor	a
	sub	e
	ld	e,a
	sbc	a,a
	sub	d
	ld	d,a
__SDivSkip2:
	call	div16       ;normal routine division
	pop	af
	ret	p
	xor	a
	sub	l
	ld	l,a
	sbc	a,a
	sub	h
	ld	h,a
	ret
