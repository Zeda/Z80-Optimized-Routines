DE_Times_A:
;Input: DE,A
;Output: A:HL is the product, C=0, B,DE unaffected, z flag set if result is zero, c flag set if A is input as 1, else nc.
;A:128~255 219+6{0,10}+{0,19}    avg=258.5   *1/2
;A:64~127  203+5{0,10}+{0,19}    avg=237.5   *1/4
;A:32~63   187+4{0,10}+{0,19}    avg=216.5   *1/8
;A:16~31   171+3{0,10}+{0,19}    avg=195.5   *1/16
;A:8~15    155+2{0,10}+{0,19}    avg=174.5   *1/32
;A:4~7     139+{0,10}+{0,19}     avg=153.5   *1/64
;A:2~3     123+{0,19}            avg=132.5   *1/128
;A:1       107cc                 avg=107     *1/256
;A:0       119cc                 avg=119     *1/256
;overall avg: 237.671875cc
    ld c,0
    ld h,d
    ld l,e
    add a,a \ jr c,mul_07
    rla \ jr c,mul_06
    rla \ jr c,mul_05
    rla \ jr c,mul_04
    rla \ jr c,mul_03
    rla \ jr c,mul_02
    rla \ jr c,mul_01
    rla
    ret c
    ld h,a
    ld l,a
    ret
mul_07:
    add hl,hl \ rla \ jr nc,$+4 \ add hl,de \ adc a,c
mul_06:
    add hl,hl \ rla \ jr nc,$+4 \ add hl,de \ adc a,c
mul_05:
    add hl,hl \ rla \ jr nc,$+4 \ add hl,de \ adc a,c
mul_04:
    add hl,hl \ rla \ jr nc,$+4 \ add hl,de \ adc a,c
mul_03:
    add hl,hl \ rla \ jr nc,$+4 \ add hl,de \ adc a,c
mul_02:
    add hl,hl \ rla \ jr nc,$+4 \ add hl,de \ adc a,c
mul_01:
    add hl,hl \ rla \ ret nc \ add hl,de \ adc a,c
    ret
