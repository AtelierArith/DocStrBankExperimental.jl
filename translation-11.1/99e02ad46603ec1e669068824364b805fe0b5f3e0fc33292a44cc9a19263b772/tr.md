```
issetequal(a, b) -> Bool
```

`a` ve `b`'nin aynı elemanlara sahip olup olmadığını belirler. `a ⊆ b && b ⊆ a` ile eşdeğerdir ancak mümkün olduğunda daha verimlidir.

Ayrıca bakınız: [`isdisjoint`](@ref), [`union`](@ref).

# Örnekler

```jldoctest
julia> issetequal([1, 2], [1, 2, 3])
false

julia> issetequal([1, 2], [2, 1])
true
```
