```
isuppercase(c::AbstractChar) -> Bool
```

Überprüft, ob ein Zeichen ein Großbuchstabe ist (gemäß der abgeleiteten Eigenschaft `Uppercase` des Unicode-Standards).

Siehe auch [`islowercase`](@ref).

# Beispiele

```jldoctest
julia> isuppercase('γ')
false

julia> isuppercase('Γ')
true

julia> isuppercase('❤')
false
```
