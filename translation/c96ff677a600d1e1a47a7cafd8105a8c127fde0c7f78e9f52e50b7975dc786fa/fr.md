```
@test_throws exception expr
```

Teste que l'expression `expr` lance `exception`. L'exception peut spécifier soit un type, une chaîne, une expression régulière, ou une liste de chaînes apparaissant dans le message d'erreur affiché, une fonction de correspondance, ou une valeur (qui sera testée pour l'égalité en comparant les champs). Notez que `@test_throws` ne prend pas en charge une forme de mot-clé terminal.

!!! compat "Julia 1.8"
    La capacité de spécifier autre chose qu'un type ou une valeur comme `exception` nécessite Julia v1.8 ou ultérieure.


# Exemples

```jldoctest
julia> @test_throws BoundsError [1, 2, 3][4]
Test Passed
      Thrown: BoundsError

julia> @test_throws DimensionMismatch [1, 2, 3] + [1, 2]
Test Passed
      Thrown: DimensionMismatch

julia> @test_throws "Try sqrt(Complex" sqrt(-1)
Test Passed
     Message: "DomainError with -1.0:\nsqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x))."
```

Dans l'exemple final, au lieu de faire correspondre une seule chaîne, cela aurait pu également être effectué avec :

  * `["Try", "Complex"]` (une liste de chaînes)
  * `r"Try sqrt\([Cc]omplex"` (une expression régulière)
  * `str -> occursin("complex", str)` (une fonction de correspondance)
