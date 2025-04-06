```
first(s::AbstractString, n::Integer)
```

Obtiene una cadena que consiste en los primeros `n` caracteres de `s`.

# Ejemplos

```jldoctest
julia> first("∀ϵ≠0: ϵ²>0", 0)
""

julia> first("∀ϵ≠0: ϵ²>0", 1)
"∀"

julia> first("∀ϵ≠0: ϵ²>0", 3)
"∀ϵ≠"
```
