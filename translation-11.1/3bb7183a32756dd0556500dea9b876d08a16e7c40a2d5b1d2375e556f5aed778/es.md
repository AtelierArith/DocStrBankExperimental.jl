```
take(iter, n)
```

Un iterador que genera como máximo los primeros `n` elementos de `iter`.

Véase también: [`drop`](@ref Iterators.drop), [`peel`](@ref Iterators.peel), [`first`](@ref), [`Base.take!`](@ref).

# Ejemplos

```jldoctest
julia> a = 1:2:11
1:2:11

julia> collect(a)
6-element Vector{Int64}:
  1
  3
  5
  7
  9
 11

julia> collect(Iterators.take(a,3))
3-element Vector{Int64}:
 1
 3
 5
```
