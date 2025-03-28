```
repeated(x[, n::Int])
```

Un itérateur qui génère la valeur `x` indéfiniment. Si `n` est spécifié, génère `x` ce nombre de fois (équivalent à `take(repeated(x), n)`).

Voir aussi [`fill`](@ref Base.fill), et comparer [`Iterators.cycle`](@ref).

# Exemples

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
