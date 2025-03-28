```
@. expr
```

Convierte cada llamada a función u operador en `expr` en una "llamada con punto" (por ejemplo, convierte `f(x)` en `f.(x)`), y convierte cada asignación en `expr` en una "asignación con punto" (por ejemplo, convierte `+=` en `.+=`).

Si deseas *evitar* agregar puntos para llamadas a funciones seleccionadas en `expr`, inserta esas llamadas a funciones con `$`. Por ejemplo, `@. sqrt(abs($sort(x)))` es equivalente a `sqrt.(abs.(sort(x)))` (sin punto para `sort`).

(`@.` es equivalente a una llamada a `@__dot__`.)

# Ejemplos

```jldoctest
julia> x = 1.0:3.0; y = similar(x);

julia> @. y = x + 3 * sin(x)
3-element Vector{Float64}:
 3.5244129544236893
 4.727892280477045
 3.4233600241796016
```
