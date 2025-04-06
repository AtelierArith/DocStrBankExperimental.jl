```
repeated(x[, n::Int])
```

Ein Iterator, der den Wert `x` für immer erzeugt. Wenn `n` angegeben ist, erzeugt er `x` so oft (entspricht `take(repeated(x), n)`).

Siehe auch [`fill`](@ref Base.fill) und vergleiche [`Iterators.cycle`](@ref).

# Beispiele

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
