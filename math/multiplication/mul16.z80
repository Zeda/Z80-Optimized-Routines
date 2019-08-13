;This was made by Runer112
;Tested by jacobly
mul16:
;BC*DE --> DEHL
; ~544.887cc as calculated in jacobly's test
;min: 214cc  (DE = 1)
;max: 667cc
;avg: 544.4507883cc   however, deferring to jacobly's result as mine may have math issues ?
;177 bytes
	ld	a,d
	ld	d,0
	ld	h,b
	ld	l,c
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit14
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit13
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit12
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit11
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit10
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit9
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit8
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit7
	ld	a,e
 	and	%11111110
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit6
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit5
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit4
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit3
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit2
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit1
	add	a,a
	jr	c,Mul_BC_DE_DEHL_Bit0
	rr	e
	ret	c
	ld	h,d
	ld	l,e
	ret

Mul_BC_DE_DEHL_Bit14:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit13
	add	hl,bc
	adc	a,d
Mul_BC_DE_DEHL_Bit13:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit12
	add	hl,bc
	adc	a,d
Mul_BC_DE_DEHL_Bit12:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit11
	add	hl,bc
	adc	a,d
Mul_BC_DE_DEHL_Bit11:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit10
	add	hl,bc
	adc	a,d
Mul_BC_DE_DEHL_Bit10:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit9
	add	hl,bc
	adc	a,d
Mul_BC_DE_DEHL_Bit9:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit8
	add	hl,bc
	adc	a,d
Mul_BC_DE_DEHL_Bit8:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit7
	add	hl,bc
	adc	a,d
Mul_BC_DE_DEHL_Bit7:
	ld	d,a
	ld	a,e
	and	%11111110
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit6
	add	hl,bc
	adc	a,0
Mul_BC_DE_DEHL_Bit6:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit5
	add	hl,bc
	adc	a,0
Mul_BC_DE_DEHL_Bit5:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit4
	add	hl,bc
	adc	a,0
Mul_BC_DE_DEHL_Bit4:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit3
	add	hl,bc
	adc	a,0
Mul_BC_DE_DEHL_Bit3:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit2
	add	hl,bc
	adc	a,0
Mul_BC_DE_DEHL_Bit2:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit1
	add	hl,bc
	adc	a,0
Mul_BC_DE_DEHL_Bit1:
	add	hl,hl
	adc	a,a
	jr	nc,Mul_BC_DE_DEHL_Bit0
	add	hl,bc
	adc	a,0
Mul_BC_DE_DEHL_Bit0:
	add	hl,hl
	adc	a,a
	jr	c,Mul_BC_DE_DEHL_FunkyCarry
	rr	e
	ld	e,a
	ret	nc
	add	hl,bc
	ret	nc
	inc	e
	ret	nz
	inc	d
	ret

Mul_BC_DE_DEHL_FunkyCarry:
	inc	d
	rr	e
	ld	e,a
	ret	nc
	add	hl,bc
	ret	nc
	inc	e
	ret
