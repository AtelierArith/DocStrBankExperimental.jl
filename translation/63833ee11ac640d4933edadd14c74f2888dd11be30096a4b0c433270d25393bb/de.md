```
^(s::Union{AbstractString,AbstractChar}, n::Integer) -> AbstractString
```

Wiederhole einen String oder ein Zeichen `n` Mal. Dies kann auch als `repeat(s, n)` geschrieben werden.

Siehe auch [`repeat`](@ref).

# Beispiele

```jldoctest
julia> "Test "^3
"Test Test Test "
```
