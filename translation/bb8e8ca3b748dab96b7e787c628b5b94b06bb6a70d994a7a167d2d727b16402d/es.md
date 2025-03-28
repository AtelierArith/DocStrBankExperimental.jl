```
last(s::AbstractString, n::Integer)
```

Obtiene una cadena que consiste en los últimos `n` caracteres de `s`.

# Ejemplos

```jldoctest
julia> last("∀ϵ≠0: ϵ²>0", 0)
""

julia> last("∀ϵ≠0: ϵ²>0", 1)
"0"

julia> last("∀ϵ≠0: ϵ²>0", 3)
"²>0"
```
