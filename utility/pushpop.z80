;Call this routine at the start of a routine and this will push HL,DE,BC, and AF
;onto the stack, set up a return so that at the end of the calling routine,
;those registers are restored.

pushpop:
;26 bytes, adds 229cc to the calling routine
  ex (sp),hl
  push de
  push bc
  push af
  push hl
  ld hl,pushpopret
  ex (sp),hl
  push hl
  push af
  ld hl,12
  add hl,sp
  ld a,(hl)
  inc hl
  ld h,(hl)
  ld l,a
  pop af
  ret
pushpopret:
  pop af
  pop bc
  pop de
  pop hl
  ret
