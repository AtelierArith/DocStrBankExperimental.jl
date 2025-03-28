```
Bool <: Integer
```

Tipo booleano, que contiene los valores `true` y `false`.

`Bool` es una especie de número: `false` es numéricamente igual a `0` y `true` es numéricamente igual a `1`. Además, `false` actúa como un "cero fuerte" multiplicativo contra [`NaN`](@ref) y [`Inf`](@ref):

```jldoctest
julia> [true, false] == [1, 0]
true

julia> 42.0 + true
43.0

julia> 0 .* (NaN, Inf, -Inf)
(NaN, NaN, NaN)

julia> false .* (NaN, Inf, -Inf)
(0.0, 0.0, -0.0)
```

Las ramas a través de [`if`](@ref) y otros condicionales solo aceptan `Bool`. No hay valores "verdaderos" en Julia.

Las comparaciones típicamente devuelven `Bool`, y las comparaciones transmitidas pueden devolver [`BitArray`](@ref) en lugar de un `Array{Bool}`.

```jldoctest
julia> [1 2 3 4 5] .< pi
1×5 BitMatrix:
 1  1  1  0  0

julia> map(>(pi), [1 2 3 4 5])
1×5 Matrix{Bool}:
 0  0  0  1  1
```

Ver también [`trues`](@ref), [`falses`](@ref), [`ifelse`](@ref).
