```
islowercase(c::AbstractChar) -> Bool
```

Überprüft, ob ein Zeichen ein Kleinbuchstabe ist (gemäß der abgeleiteten Eigenschaft `Lowercase` des Unicode-Standards).

Siehe auch [`isuppercase`](@ref).

# Beispiele

```jldoctest
julia> islowercase('α')
true

julia> islowercase('Γ')
false

julia> islowercase('❤')
false
```
