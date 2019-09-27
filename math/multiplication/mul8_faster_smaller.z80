H_Times_E:
mul8:
;Inputs: H,E
;Outputs: HL is the product, D is 0
;Destroys: A
;187+6{0,6}+{0,15}
;min: 187cc
;max: 238cc
;avg: 212.5cc
;35 bytes
    ld d,0
    sla h
    sbc a,a
    and e
    ld l,a
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ jr nc,$+3 \ add hl,de
    add hl,hl \ ret nc \ add hl,de \ ret
