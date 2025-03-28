```
@test_throws exception expr
```

Prueba que la expresión `expr` lanza `exception`. La excepción puede especificar ya sea un tipo, una cadena, una expresión regular, o una lista de cadenas que ocurren en el mensaje de error mostrado, una función de coincidencia, o un valor (que será probado por igualdad comparando campos). Ten en cuenta que `@test_throws` no soporta una forma de palabra clave al final.

!!! compat "Julia 1.8"
    La capacidad de especificar cualquier cosa que no sea un tipo o un valor como `exception` requiere Julia v1.8 o posterior.


# Ejemplos

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

En el último ejemplo, en lugar de coincidir con una sola cadena, podría haberse realizado alternativamente con:

  * `["Try", "Complex"]` (una lista de cadenas)
  * `r"Try sqrt\([Cc]omplex"` (una expresión regular)
  * `str -> occursin("complex", str)` (una función de coincidencia)
