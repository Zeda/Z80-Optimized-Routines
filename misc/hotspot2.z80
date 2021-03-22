;This version works like the hotspot routine, but takes width and height args
;instead of a second coord
;----------Hot spot detection-----------
;inputs: b,c (upper-left x and y coordinates)
;        d,e (width and height)
;        h,l (current x,y)
;output: "c" flag [either true (set) or false (reset)]

; This routine checks if a point (H,L) is within a box defined by (B,C) and (D,E)
hdetectrect:
  ld a,h
  sub b
  cp d
  ret nc
  ld a,l
  sub c
  cp e
  ret
