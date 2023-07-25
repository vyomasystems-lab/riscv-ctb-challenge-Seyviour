# GENERATING 10 ILLEGAL INSTUCTION EXCEPTIONS

AAPG provides the capability to automatically generate exceptions (and appropriate exception handlers) by configuring the following highlighted `ecause02` options appropriately -- `2` is the standard `mcause` for illegal instruction exceptions:

```
    exception-generation:
        ecause00: 0
        ecause01: 0
        ecause02: 10
        ...

```

```
    program-macro:
        pre_program_macro: "add x0,x0,x0"
        post_program_macro: "add x0,x0,x0"
        pre_branch_macro: "add x0,x0,x0"
        post_branch_macro: "add x0,x0,x0"
        ecause00: "random"
        ecause01: "random"
        ***ecause02: "random"***
        ...

```

