```
Test.Error <: Test.Result
```

Die Testbedingung konnte aufgrund einer Ausnahme nicht ausgewertet werden oder sie wurde auf etwas anderes als ein [`Bool`](@ref) ausgewertet. Im Fall von `@test_broken` wird es verwendet, um anzuzeigen, dass ein unerwartetes `Pass` `Result` aufgetreten ist.
