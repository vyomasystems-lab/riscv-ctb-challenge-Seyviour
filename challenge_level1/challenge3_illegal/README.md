# BUG-FIX REPORT

## BUG

The test programme enters an unintended infinite loop.

## CAUSE

There is an intentionally inserted illegal instruction in the test (`.word 0`). This illegal instruction triggers an exception that is handled by the `mtvec_hanlder` subroutine. It is in this subroutine that an error occurs -- the expected behaviour is that the subroutine returns to the instruction after the address specified in `mepc` i.e there should be a line that makes `mepc` point to the next instruction. This does not occur in the original test, causing the exception handler to return to the illegal instruction, triggering an infinite loop.

## FIX

In  `mtvec_handler`, update `mepc` to point to the next valid instruction. This is achieved with the following lines of code: 
```
    csrr t0, mepc  
    addi t0, t0, 4  
    csrw mepc, t0  
```

