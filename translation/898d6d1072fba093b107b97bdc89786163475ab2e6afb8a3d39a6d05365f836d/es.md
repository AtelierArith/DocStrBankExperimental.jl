```
repeated(x[, n::Int])
```

Un iterador que genera el valor `x` para siempre. Si se especifica `n`, genera `x` esa cantidad de veces (equivalente a `take(repeated(x), n)`).

Véase también [`fill`](@ref Base.fill), y compare [`Iterators.cycle`](@ref).

# Ejemplos

```jldoctest
julia> a = Iterators.repeated([1 2], 4);

julia> collect(a)
4-element Vector{Matrix{Int64}}:
 [1 2]
 [1 2]
 [1 2]
 [1 2]

julia> ans == fill([1 2], 4)
true

julia> Iterators.cycle([1 2], 4) |> collect |> println
[1, 2, 1, 2, 1, 2, 1, 2]
```
