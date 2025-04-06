```
@sprintf("%Fmt", args...)
```

Retourne la sortie formatée de [`@printf`](@ref) sous forme de chaîne.

# Exemples

```jldoctest
julia> @sprintf "this is a %s %15.1f" "test" 34.567
"this is a test            34.6"
```
