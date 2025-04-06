```
@test_skip ex
@test_skip f(args...) key=val ...
```

Marque un test qui ne doit pas être exécuté mais qui doit être inclus dans le rapport de résumé des tests comme `Broken`. Cela peut être utile pour des tests qui échouent de manière intermittente, ou des tests de fonctionnalités pas encore implémentées. Cela équivaut à [`@test ex skip=true`](@ref @test).

La forme `@test_skip f(args...) key=val...` fonctionne comme pour la macro `@test`.

# Exemples

```jldoctest
julia> @test_skip 1 == 2
Test Broken
  Skipped: 1 == 2

julia> @test_skip 1 == 2 atol=0.1
Test Broken
  Skipped: ==(1, 2, atol = 0.1)
```
