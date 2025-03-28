```
last(s::AbstractString, n::Integer)
```

Obtenez une chaîne composée des derniers `n` caractères de `s`.

# Exemples

```jldoctest
julia> last("∀ϵ≠0: ϵ²>0", 0)
""

julia> last("∀ϵ≠0: ϵ²>0", 1)
"0"

julia> last("∀ϵ≠0: ϵ²>0", 3)
"²>0"
```
