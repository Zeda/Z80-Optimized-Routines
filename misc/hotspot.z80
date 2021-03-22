;License: https://www.cemetech.net/projects/uti/viewtopic.php?t=1279
;DarkerLine
;----------Hot spot detection-----------
;inputs: b,c (first x and y cor)
;        d,e (last x and y cor)
;        h,l (current x,y)
;output: "c" flag [either true (set) or false (reset)]
;
; This routine checks if a point (H,L) is within a box defined by (B,C) and (D,E)
hdetect:
  ld a,h
  cp b
  ccf
  ret nc
  cp d
  ret nc
  ld a,l
  cp c
  ccf
  ret nc
  cp e
  ret
