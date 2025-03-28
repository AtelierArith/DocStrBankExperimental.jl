```
filter(f)
```

Crea una función que filtra sus argumentos con la función `f` usando [`filter`](@ref), es decir, una función equivalente a `x -> filter(f, x)`.

La función devuelta es de tipo `Base.Fix1{typeof(filter)}`, que se puede usar para implementar métodos especializados.

# Ejemplos

```jldoctest
julia> (1, 2, Inf, 4, NaN, 6) |> filter(isfinite)
(1, 2, 4, 6)

julia> map(filter(iseven), [1:3, 2:4, 3:5])
3-element Vector{Vector{Int64}}:
 [2]
 [2, 4]
 [4]
```

!!! compat "Julia 1.9"
    Este método requiere al menos Julia 1.9.

