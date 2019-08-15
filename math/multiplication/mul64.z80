;This multiplies two 64-bit integers and returns a 128-bit result.
;This requires the following routines:
;   mul32
;       Inputs: DEHL, BCIX
;       Output: stored at z32_0, little-endian
;   mov8
;       basically any routine that works like 8 LDI instructions.
;
;   Defined:
;       inp64_1 is where the first 64-bit multiplicand is located, little-endian
;       inp64_2 is where the second 64-bit multiplicand is located, little-endian
;       out128  is where the 128-bit result is stored
;   Uses 8 additional bytes after out128

mul64:
;multiplies the 64-bit integers at inp64_1 and inp64_2
;stores the 128-bit (16-byte) result at out128
;
;min: 1740+3*min(mul32)
;     5631cc
;max: 1901+3*max(mul32)
;     10013cc
;avg: 1797+3*avg(mul32) + 9572881/2^24
;    ~8720.733cc
;uses 24 bytes at out128
z64_0 = out128
z64_2 = z64_0+8
z32_0 = z64_2+8

  ld de,(inp64_1+6)
  ld hl,(inp64_1+4)
  ld bc,(inp64_2+6)
  ld ix,(inp64_2+4)
  call mul32
  ;copy the 8 bytes at z32_0 to z64_2
  ld hl,z32_0
  ld de,z64_2
  call mov8

  ld de,(inp64_1+2)
  ld hl,(inp64_1)
  ld bc,(inp64_2+2)
  ld ix,(inp64_2)
  call mul32
  ;copy the 8 bytes at z32_0 to z64_0
  ld hl,z32_0
  ld de,z64_0
  call mov8

;now I need to subtract the 32-bit digits from each other
  xor a
  ld hl,(inp64_1)
  ld bc,(inp64_1+4)
  sbc hl,bc
  ex de,hl
  ld hl,(inp64_1+2)
  ld bc,(inp64_1+6)
  sbc hl,bc
  jr nc,+_
  ld b,a \ sub e \ ld e,a
  ld a,b \ sbc a,d \ ld d,a
  ld a,b \ sbc a,l \ ld l,a
  ld a,b \ sbc a,h \ ld h,a
  ld a,b
_:
  rla
  push hl   ;top byte
  push de

  ld hl,(inp64_2)
  ld bc,(inp64_2+4)
  sbc hl,bc
  ex de,hl
  ld hl,(inp64_2+2)
  ld bc,(inp64_2+6)
  sbc hl,bc
  jr nc,+_
  ld c,a
  xor a
  ld b,a
  sub e \ ld e,a
  ld a,b \ sbc a,d \ ld d,a
  ld a,b \ sbc a,l \ ld l,a
  ld a,b \ sbc a,h \ ld h,a
  ld a,c
  inc a
_:
  ex de,hl
  pop ix
  pop bc
  push af
  call mul32
  pop af    ;holds the sign in the low bit

  rra
  jp c,mul64_add
;need to perform z0+z2-result
  xor a
  ld hl,(z64_0)
  ld de,(z64_2)
  add hl,de
  ld (inp64_1),hl
  ld hl,(z64_0+2)
  ld de,(z64_2+2)
  adc hl,de
  ld (inp64_1+2),hl
  ld hl,(z64_0+4)
  ld de,(z64_2+4)
  adc hl,de
  ld (inp64_1+4),hl
  ld hl,(z64_0+6)
  ld de,(z64_2+6)
  adc hl,de
  ld (inp64_1+6),hl
  rla
;now need to subtract
  ld hl,(inp64_1)
  ld de,(z32_0)
  sbc hl,de
  ld (inp64_1),hl
  ld hl,(inp64_1+2)
  ld de,(z32_0+2)
  sbc hl,de
  ld (inp64_1+2),hl
  ld hl,(inp64_1+4)
  ld de,(z32_0+4)
  sbc hl,de
  ld (inp64_1+4),hl
  ld hl,(inp64_1+6)
  ld de,(z32_0+6)
  sbc hl,de
  ld (inp64_1+6),hl
  sbc a,0
mul64_final:
;now need to add it back in
  ld hl,(z64_0+4)
  ld de,(inp64_1)
  add hl,de
  ld (z64_0+4),hl
  ld hl,(z64_0+6)
  ld de,(inp64_1+2)
  adc hl,de
  ld (z64_0+6),hl
  ld hl,(z64_0+8)
  ld de,(inp64_1+4)
  adc hl,de
  ld (z64_0+8),hl
  ld hl,(z64_0+10)
  ld de,(inp64_1+6)
  adc hl,de
  ld (z64_0+10),hl
  ld hl,z64_0+12
  adc a,(hl)
  ld (hl),a
  ret nc
  inc hl \ inc (hl) \ ret nz
  inc hl \ inc (hl) \ ret nz
  inc hl \ inc (hl) \ ret
mul64_add:
;add to the current result
;z0+z2+result
  xor a
  ld hl,(z64_0)
  ld de,(z64_2)
  add hl,de
  ld (inp64_1),hl
  ld hl,(z64_0+2)
  ld de,(z64_2+2)
  adc hl,de
  ld (inp64_1+2),hl
  ld hl,(z64_0+4)
  ld de,(z64_2+4)
  adc hl,de
  ld (inp64_1+4),hl
  ld hl,(z64_0+6)
  ld de,(z64_2+6)
  adc hl,de
  ld (inp64_1+6),hl
  rla
;now need to subtract
  ld hl,(inp64_1)
  ld de,(z32_0)
  add hl,de
  ld (inp64_1),hl
  ld hl,(inp64_1+2)
  ld de,(z32_0+2)
  adc hl,de
  ld (inp64_1+2),hl
  ld hl,(inp64_1+4)
  ld de,(z32_0+4)
  adc hl,de
  ld (inp64_1+4),hl
  ld hl,(inp64_1+6)
  ld de,(z32_0+6)
  adc hl,de
  ld (inp64_1+6),hl
  adc a,0
  jp mul64_final
