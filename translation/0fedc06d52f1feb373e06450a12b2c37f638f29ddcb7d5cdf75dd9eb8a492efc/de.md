```
isless(a::AbstractString, b::AbstractString) -> Bool
```

Überprüfen, ob der String `a` im alphabetischen Vergleich (technisch gesehen, im lexikografischen Vergleich nach Unicode-Codepunkten) vor dem String `b` kommt.

# Beispiele

```jldoctest
julia> isless("a", "b")
true

julia> isless("β", "α")
false

julia> isless("a", "a")
false
```
