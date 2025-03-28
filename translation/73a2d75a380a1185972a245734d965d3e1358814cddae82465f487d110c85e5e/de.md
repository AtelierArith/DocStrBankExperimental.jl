```
@test_broken ex
@test_broken f(args...) key=val ...
```

Kennzeichnet einen Test, der bestehen sollte, aber derzeit konstant fehlschlägt. Testet, ob der Ausdruck `ex` zu `false` evaluiert oder eine Ausnahme verursacht. Gibt ein `Broken` `Result` zurück, wenn dies der Fall ist, oder ein `Error` `Result`, wenn der Ausdruck zu `true` evaluiert. Dies entspricht [`@test ex broken=true`](@ref @test).

Die Form `@test_broken f(args...) key=val...` funktioniert wie bei dem `@test`-Makro.

# Beispiele

```jldoctest
julia> @test_broken 1 == 2
Test Broken
  Expression: 1 == 2

julia> @test_broken 1 == 2 atol=0.1
Test Broken
  Expression: ==(1, 2, atol = 0.1)
```
