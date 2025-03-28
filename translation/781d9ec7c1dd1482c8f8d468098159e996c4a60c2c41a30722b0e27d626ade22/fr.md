```
IOBuffer(string::String)
```

Crée un `IOBuffer` en lecture seule sur les données sous-jacentes de la chaîne donnée.

# Exemples

```jldoctest
julia> io = IOBuffer("Haho");

julia> String(take!(io))
"Haho"

julia> String(take!(io))
"Haho"
```
