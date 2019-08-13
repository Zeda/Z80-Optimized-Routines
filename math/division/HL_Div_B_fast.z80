HL_Div_B:
;I'm not postive on the timing. 
;min: 203
;max: 308
;avg: 236.125
  add hl,hl
  ld a,h
  jr c,div16_8_2_0
  cp b \ jr c,$+4 \ sub b \ inc l
  sla l \ rla \ jr c,div16_8_2_1
div16_8_1_1:
  cp b \ jr c,$+4 \ sub b \ inc l
  sla l \ rla \ jr c,div16_8_2_2
div16_8_1_2:
  cp b \ jr c,$+4 \ sub b \ inc l
  sla l \ rla \ jr c,div16_8_2_3
div16_8_1_3:
  cp b \ jr c,$+4 \ sub b \ inc l
  sla l \ rla \ jr c,div16_8_2_4
div16_8_1_4:
  cp b \ jr c,$+4 \ sub b \ inc l
  sla l \ rla \ jr c,div16_8_2_5
div16_8_1_5:
  cp b \ jr c,$+4 \ sub b \ inc l
  sla l \ rla \ jr c,div16_8_2_6
div16_8_1_6:
  cp b \ jr c,$+4 \ sub b \ inc l
  sla l \ rla \ jr c,div16_8_2_7
div16_8_1_7:
  cp b \ ret c \ sub b \ inc l
  ret

div16_8_2_0:
  sub b \ rl l \ rla \ jr nc,div16_8_1_1
div16_8_2_1:
  sub b \ rl l \ rla \ jr nc,div16_8_1_2
div16_8_2_2:
  sub b \ rl l \ rla \ jr nc,div16_8_1_3
div16_8_2_3:
  sub b \ rl l \ rla \ jr nc,div16_8_1_4
div16_8_2_4:
  sub b \ rl l \ rla \ jr nc,div16_8_1_5
div16_8_2_5:
  sub b \ rl l \ rla \ jr nc,div16_8_1_6
div16_8_2_6:
  sub b \ rl l \ rla \ jr nc,div16_8_1_7
div16_8_2_7:
  sub b \ inc l
  ret