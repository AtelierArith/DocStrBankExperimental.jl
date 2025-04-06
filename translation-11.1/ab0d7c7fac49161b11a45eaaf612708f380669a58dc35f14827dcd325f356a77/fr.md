```
summary(io::IO, x)
str = summary(x)
```

Imprime dans un flux `io`, ou retourne une chaîne `str`, donnant une brève description d'une valeur. Par défaut, retourne `string(typeof(x))`, par exemple [`Int64`](@ref).

Pour les tableaux, retourne une chaîne d'informations sur la taille et le type, par exemple `10-element Array{Int64,1}`.

# Exemples

```jldoctest
julia> summary(1)
"Int64"

julia> summary(zeros(2))
"2-element Vector{Float64}"
```
