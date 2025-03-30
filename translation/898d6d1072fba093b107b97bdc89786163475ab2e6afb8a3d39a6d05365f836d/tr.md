```
repeated(x[, n::Int])
```

Sonsuz bir şekilde `x` değerini üreten bir iteratör. Eğer `n` belirtilirse, `x` o kadar kez üretilir (bu, `take(repeated(x), n)` ile eşdeğerdir).

Ayrıca [`fill`](@ref Base.fill) ve [`Iterators.cycle`](@ref) ile karşılaştırın.

# Örnekler

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
