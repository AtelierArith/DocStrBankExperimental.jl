```
@sprintf("%Fmt", args...)
```

Gibt die formatierte Ausgabe von [`@printf`](@ref) als Zeichenfolge zurück.

# Beispiele

```jldoctest
julia> @sprintf "dies ist ein %s %15.1f" "test" 34.567
"dies ist ein test            34.6"
```
