;Reverses the bits in A
;author: calcmaniac84

reversea:
;input: Byte in A
;output: Reversed byte in A
;destroys B
;Clock cycles: 66
;Bytes: 18
 ld b,a
 rrca
 rrca
 xor b
 and %10101010
 xor b
 ld b,a
 rrca
 rrca
 rrca
 rrca
 xor b
 and %01100110
 xor b
 rrca
 ret
