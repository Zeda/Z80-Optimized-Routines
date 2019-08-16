;Adapted from Axe

sqrtfixed_88:
;Inputs: A.C
;Output: D.E contains the squareroot
;speed: 1482+12{0,17}
;min: 1482cc
;max: 1686cc
;avg: 1584cc
;35 bytes
	ld	b,12
	ld	de,0
	ld	h,d
	ld	l,e
__Sqrt88Loop:
	sub	$40
	sbc	hl,de
	jr	nc,__Sqrt88Skip
	add	a,$40
	adc	hl,de
__Sqrt88Skip:
	ccf
	rl	e
	rl	d
	sla	c
	rla
	adc	hl,hl
	sla	c
	rla
	adc 	hl,hl
	djnz	__Sqrt88Loop
	ret
