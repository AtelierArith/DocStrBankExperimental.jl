```
first(s::AbstractString, n::Integer)
```

Obtenez une chaîne composée des premiers `n` caractères de `s`.

# Exemples

```jldoctest
julia> first("∀ϵ≠0: ϵ²>0", 0)
""

julia> first("∀ϵ≠0: ϵ²>0", 1)
"∀"

julia> first("∀ϵ≠0: ϵ²>0", 3)
"∀ϵ≠"
```
