```
@test ex
@test f(args...) key=val ...
@test ex broken=true
@test ex skip=true
```

Testez que l'expression `ex` évalue à `true`. Si exécuté à l'intérieur d'un `@testset`, renvoyez un `Pass` `Result` si c'est le cas, un `Fail` `Result` s'il est `false`, et un `Error` `Result` s'il ne peut pas être évalué. Si exécuté en dehors d'un `@testset`, lancez une exception au lieu de renvoyer `Fail` ou `Error`.

# Exemples

```jldoctest
julia> @test true
Test Passed

julia> @test [1, 2] + [2, 1] == [3, 3]
Test Passed
```

La forme `@test f(args...) key=val...` est équivalente à écrire `@test f(args..., key=val...)` ce qui peut être utile lorsque l'expression est un appel utilisant une syntaxe infixe telle que des comparaisons approximatives :

```jldoctest
julia> @test π ≈ 3.14 atol=0.01
Test Passed
```

Ceci est équivalent au test moins élégant `@test ≈(π, 3.14, atol=0.01)`. Il est interdit de fournir plus d'une expression à moins que la première soit une expression d'appel et que le reste soit des affectations (`k=v`).

Vous pouvez utiliser n'importe quelle clé pour les arguments `key=val`, sauf pour `broken` et `skip`, qui ont des significations spéciales dans le contexte de `@test` :

  * `broken=cond` indique un test qui devrait réussir mais échoue actuellement de manière cohérente lorsque `cond==true`.  Tests que l'expression `ex` évalue à `false` ou provoque une exception.  Renvoie un `Broken` `Result` si c'est le cas, ou un `Error` `Result` si l'expression évalue à `true`.  Le `@test ex` régulier est évalué lorsque `cond==false`.
  * `skip=cond` marque un test qui ne devrait pas être exécuté mais qui devrait être inclus dans le rapport de résumé des tests comme `Broken`, lorsque `cond==true`.  Cela peut être utile pour des tests qui échouent de manière intermittente, ou des tests de fonctionnalités pas encore implémentées. Le `@test ex` régulier est évalué lorsque `cond==false`.

# Exemples

```jldoctest
julia> @test 2 + 2 ≈ 6 atol=1 broken=true
Test Broken
  Expression: ≈(2 + 2, 6, atol = 1)

julia> @test 2 + 2 ≈ 5 atol=1 broken=false
Test Passed

julia> @test 2 + 2 == 5 skip=true
Test Broken
  Skipped: 2 + 2 == 5

julia> @test 2 + 2 == 4 skip=false
Test Passed
```

!!! compat "Julia 1.7"
    Les arguments de mot-clé `broken` et `skip` nécessitent au moins Julia 1.7.

