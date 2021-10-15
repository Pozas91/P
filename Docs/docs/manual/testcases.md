P Test cases are used to define different finite scenarios under which we would like to
check the correctness of our system.

???+ note "P Test Cases Grammar"

    ```
    testcase
    | test iden [main=iden] : modExpr ;                  # TestDecl
    ;
    ```
    `modExpr` represent the P module defined using the module expressions described in [P Module System](modulesystem.md)

### Test Declaration

P allows the programmers to write different finite model checking scenarios that check the correctness of the module (or system) under test. The system module to be tested is unioned with different environment modules (or test harnesses) to check its correctness under different inputs scenarios generated by the environment modules. Each test case is automatically discharged by the P Checker.

**Syntax:**: `test tName [main=mName] : module_under_test ;`

`tName` is the name of the test case, mName is the name of the **main** machine where the execution of the system starts, and `module_under_test` is the module to be tested.

!!! info "Properties checked for a Test Case"

    For each testcase, the P checker by default asserts that for each execution of the system (or `module_under_test`): (1) there are no `unhandled event` exceptions, (2) all local assertions in the program hold, (3) there are no deadlocks and finally (4) based on the [specification monitors that are attached](modulesystem.md#assert-monitors-module) to the module, the safety and liveness properties asserted by the monitors always hold. 
