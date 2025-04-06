```
@test_skip ex
@test_skip f(args...) key=val ...
```

Markiert einen Test, der nicht ausgeführt werden soll, aber in der Testzusammenfassung als `Broken` aufgeführt werden sollte. Dies kann nützlich sein für Tests, die sporadisch fehlschlagen, oder Tests von noch nicht implementierten Funktionen. Dies entspricht [`@test ex skip=true`](@ref @test).

Die Form `@test_skip f(args...) key=val...` funktioniert wie bei dem `@test`-Makro.

# Beispiele

```jldoctest
julia> @test_skip 1 == 2
Test Broken
  Skipped: 1 == 2

julia> @test_skip 1 == 2 atol=0.1
Test Broken
  Skipped: ==(1, 2, atol = 0.1)
```
