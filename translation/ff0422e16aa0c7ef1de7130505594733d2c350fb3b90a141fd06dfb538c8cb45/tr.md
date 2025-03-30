```
isdisjoint(a, b) -> Bool
```

Koleksiyonların `a` ve `b` ayrık olup olmadığını belirleyin. `isempty(a ∩ b)` ile eşdeğerdir ancak mümkün olduğunda daha verimlidir.

Ayrıca bkz: [`intersect`](@ref), [`isempty`](@ref), [`issetequal`](@ref).

!!! compat "Julia 1.5"
    Bu fonksiyon en az Julia 1.5 gerektirir.


# Örnekler

```jldoctest
julia> isdisjoint([1, 2], [2, 3, 4])
false

julia> isdisjoint([3, 1], [2, 4])
true
```
