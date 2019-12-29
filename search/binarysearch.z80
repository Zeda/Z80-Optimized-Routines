;Requires `call_ix` routine that looks like:
;   call_ix:
;       jp (ix)
;
;IX points to a comparison routine that takes as input:
;   HL points to the input element to find
;   DE is the element to compare to
;Outputs are:
;   carry set if the HL element is less than the DE element
;   carry reset if the HL element is greater than or equal to the DE element
;   z set if the HL element is equal to the DE element
;   nz set if the HL element is not equal to the DE element
;
;This is useful if you have a table of pointers to strings, and want to find a
;string in the array. See the end of this file for an example.
;

binarysearch:
;This is a general-purpose binary search routine.
;
;Inputs:
;   BC is the element to find
;   HL is the number of elements
;   IX points to a callback routine that compares the input element
;Outputs:
;   DE is the matching element index
;   z means match found
;   nz means no match
;       In this case, DE is interpreted as where the match should have been
;Destroys:
;   AF, DE
;RAM needed:
;   10 bytes of stack space (4 pushes and a call)
;
  ld de,-1
binarysearch_loop_inc_lower:
  inc de
binarysearch_loop:
  push hl
  push de
  or a
  sbc hl,de
  jr z,binarysearch_nomatch
  rr h
  rr l
  add hl,de
  ld d,h
  ld e,l
  push hl   ;test index
  push bc   ;input
  ld h,b
  ld l,c
  call call_ix
  pop bc    ;input
  jr nc,binarysearch_input_bigger_or_equal
  pop hl    ;test index is the new upper index
  pop de    ;restore the lower index
  pop af    ;dummy pop
  jr binarysearch_loop

binarysearch_input_bigger_or_equal:
  pop de    ;test index +1 is the new lower index
  pop hl    ;dummy pop
  pop hl    ;restore upper index
  jr nz,binarysearch_loop_inc_lower
  ;a match was found
  ;DE is left as the index
  ret

binarysearch_nomatch:
  pop de    ;lower index
  pop hl    ;upper index (also lower index and test index)
  or 1
  ret


; Example, suppose we have a table of pointers to strings and HL points to a
; string that we want to find.
;
;     ; get the index in BC
;     ld b,h
;     ld c,l
;     ld hl,(string_LUT_end-string_LUT)/2
;     ld ix,my_compare_routine
;     call binarysearch
;     jr z,found
;     jr not_found
;
;     ...
;
; my_compare_routine:
; ;Inputs: HL points to the string to compare to, DE is the index
;
;     ; Look for the string's pointer in the LUT
;     ex de,hl
;     add hl,hl
;     ld bc,string_LUT
;     add hl,bc
;
;     ; load the pointer into HL
;     ld a,(hl)
;     inc hl
;     ld h,(hl)
;     ld l,a
;
;     ; DE points to the string to find (input)
;     ; HL points to the string to compare to
;     ; want to return
;     ;   nc if input is greater or equal
;     ;   c if input is smaller
;     ;   z if they are equal
;     ;   nz if they are not equal
;     jp cpstr
;
; call_ix:
;     jp (ix)
