# BUGFIX REPORT

## BUG
Test loops indefinitely.

## CAUSE
There is no bound on the area of memory that is accessed during tests. More specifically, there are three test cases (each with three words). All test cases pass but the test goes on to access uninitialized memory outside the test cases. These uninitialized memory spaces hold the value `0x0` and thus function as phantom test cases that always pass `(0x0 = 0x0 + 0x0)`, causing the programme to loop indefinitely.

## FIX
* Set the register `t5` to the number of expected test cases before entering `loop`
* Decrement `t5` after each test case
* branch to `test_end` when `t5 == 0`

