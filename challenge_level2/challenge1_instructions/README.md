# CHALLENGE 2.1 (INSTRUCTIONS) -- BUG FIX REPORT

## BUG

Test program fails due to invalid instructions. Errors are of the form: `unrecognized opcode 'remuw t4,s7,a3'`

## CAUSE
The rv32i.yaml file passed to AAPG incorrectly configures it to generate 64-bit multiplication instructions. The target platform (RV32I) does not implement these instructions and thus throws 'unrecognized opcode' errors.

## BUG FIX
Changing the config in the yaml file to disallow the generation of 64-bit instructions fixes this problem.

~~`rel_rv64m: 10`~~  `rel_rv64m: 0`