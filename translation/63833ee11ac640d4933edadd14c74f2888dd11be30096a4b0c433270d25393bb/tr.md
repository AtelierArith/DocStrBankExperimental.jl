```
^(s::Union{AbstractString,AbstractChar}, n::Integer) -> AbstractString
```

Bir dizeyi veya karakteri `n` kez tekrarlayın. Bu aynı zamanda `repeat(s, n)` olarak da yazılabilir.

Ayrıca bkz. [`repeat`](@ref).

# Örnekler

```jldoctest
julia> "Test "^3
"Test Test Test "
```
