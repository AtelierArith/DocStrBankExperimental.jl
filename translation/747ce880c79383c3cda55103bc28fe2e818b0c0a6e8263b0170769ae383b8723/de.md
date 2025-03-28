```
chomp(s::AbstractString) -> SubString
```

Entfernt ein einzelnes abschließendes Zeilenumbruchzeichen von einem String.

Siehe auch [`chop`](@ref).

# Beispiele

```jldoctest
julia> chomp("Hello\n")
"Hello"
```
