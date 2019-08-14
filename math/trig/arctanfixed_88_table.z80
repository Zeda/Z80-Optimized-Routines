arctan_88:
;Input:
;   D.E
;Output: atan(D.E)->D.E
   push de
   ld a,d
   or a
   jp p,$+5
   neg
   ld d,a
   dec a
   jr nz,checkneedinv
   inc e \ dec e \ jr nz,checkneedinv
   pop af \ rla \ ld de,201 \ ret nc \ ld de,-201 \ ret
checkneedinv:
   inc a
   call nz,DEgt1_Inv
;0.E is the value to atan
   ld hl,adjustatan
   push hl
   ld a,e
   cp 46 \ ret c
   dec a \ cp 42h \ ret c
   dec a \ cp 4Eh \ ret c
   dec a \ cp 57h \ ret c
   dec a \ cp 5Eh \ ret c
   dec a \ cp 64h \ ret c
   dec a \ cp 6Ah \ ret c
   dec a \ cp 6Fh \ ret c
   sub 6Fh \ ld e,a
   ld hl,atanlut
   add hl,de
   ld a,(hl)
   ret
adjustatan:
   ld e,a
   pop bc
   ld a,b
   or a
   jp p,$+5
   neg
   jr z,$+9
   ld hl,402
   or a
   sbc hl,de
   ex de,hl
   rl b
   ret nc
   xor a
   sub e
   ld e,a
   sbc a,a
   sub d
   ld d,a
   ret


DEgt1_Inv:
;Works if DE>1
   ld hl,256
   ld b,8
InvLoop:
   add hl,hl
   sbc hl,de
   jr nc,$+3
   add hl,de
   adc a,a
   djnz InvLoop
    cpl
   ld e,a
    ld d,b
    ret
atanlut:
.db $6F
.db $6F
.db $70
.db $71
.db $72
.db $73
.db $73
.db $74
.db $75
.db $76
.db $77
.db $77
.db $78
.db $79
.db $7A
.db $7B
.db $7B
.db $7C
.db $7D
.db $7E
.db $7F
.db $7F
.db $80
.db $81
.db $82
.db $82
.db $83
.db $84
.db $85
.db $85
.db $86
.db $87
.db $88
.db $88
.db $89
.db $8A
.db $8B
.db $8B
.db $8C
.db $8D
.db $8E
.db $8E
.db $8F
.db $90
.db $90
.db $91
.db $92
.db $93
.db $93
.db $94
.db $95
.db $95
.db $96
.db $97
.db $97
.db $98
.db $99
.db $9A
.db $9A
.db $9B
.db $9C
.db $9C
.db $9D
.db $9E
.db $9E
.db $9F
.db $A0
.db $A0
.db $A1
.db $A2
.db $A2
.db $A3
.db $A3
.db $A4
.db $A5
.db $A5
.db $A6
.db $A7
.db $A7
.db $A8
.db $A9
.db $A9
.db $AA
.db $AA
.db $AB
.db $AC
.db $AC
.db $AD
.db $AD
.db $AE
.db $AF
.db $AF
.db $B0
.db $B0
.db $B1
.db $B2
.db $B2
.db $B3
.db $B3
.db $B4
.db $B5
.db $B5
.db $B6
.db $B6
.db $B7
.db $B7
.db $B8
.db $B9
.db $B9
.db $BA
.db $BA
.db $BB
.db $BB
.db $BC
.db $BC
.db $BD
.db $BE
.db $BE
.db $BF
.db $BF
.db $C0
.db $C0
.db $C1
.db $C1
.db $C2
.db $C2
.db $C3
.db $C3
.db $C4
.db $C4
.db $C5
.db $C6
.db $C6
.db $C7
.db $C7
.db $C8
.db $C8
.db $C9
