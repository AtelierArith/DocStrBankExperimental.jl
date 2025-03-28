```
@test_broken ex
@test_broken f(args...) key=val ...
```

Indique un test qui devrait réussir mais échoue actuellement de manière constante. Teste si l'expression `ex` évalue à `false` ou provoque une exception. Renvoie un `Result` `Broken` si c'est le cas, ou un `Result` `Error` si l'expression évalue à `true`. Cela équivaut à [`@test ex broken=true`](@ref @test).

La forme `@test_broken f(args...) key=val...` fonctionne comme pour la macro `@test`.

# Exemples

```jldoctest
julia> @test_broken 1 == 2
Test Broken
  Expression: 1 == 2

julia> @test_broken 1 == 2 atol=0.1
Test Broken
  Expression: ==(1, 2, atol = 0.1)
```
