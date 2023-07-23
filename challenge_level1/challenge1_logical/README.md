# BUG-FIX REPORT

## BUGS
* On line 25584, the `andi` instruction is used wrongly with a register operand (`andi s5, t1, s0`)
* On line 15855, an illegal register operand `z4` is used with the `and` instruction (`and s7, ra, z4`)

## FIX
Commenting out the mentioned lines is sufficient to make the test compile and run successfully. 