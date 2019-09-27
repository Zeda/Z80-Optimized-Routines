H_Times_E:
mul8:
;Inputs: H,E
;Outputs: HL is the product, D is 0
;190+6{0,6}+{0,15}+{0,1}
;min: 190cc
;max: 242
;avg: 216
;36 bytes
    ld d,0
    ld l,d
    sla h \ jr nc,$+3 \ ld l,e
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ ret nc \ add hl,de \ ret
