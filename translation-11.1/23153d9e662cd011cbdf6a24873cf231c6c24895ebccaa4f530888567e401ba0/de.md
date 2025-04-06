```
map(f, c...) -> Sammlung
```

Transformiere die Sammlung `c`, indem `f` auf jedes Element angewendet wird. Bei mehreren Sammlungsargumenten `f` elementweise anwenden und stoppen, wenn eine von ihnen erschöpft ist.

Siehe auch [`map!`](@ref), [`foreach`](@ref), [`mapreduce`](@ref), [`mapslices`](@ref), [`zip`](@ref), [`Iterators.map`](@ref).

# Beispiele

```jldoctest
julia> map(x -> x * 2, [1, 2, 3])
3-element Vector{Int64}:
 2
 4
 6

julia> map(+, [1, 2, 3], [10, 20, 30, 400, 5000])
3-element Vector{Int64}:
 11
 22
 33
```
