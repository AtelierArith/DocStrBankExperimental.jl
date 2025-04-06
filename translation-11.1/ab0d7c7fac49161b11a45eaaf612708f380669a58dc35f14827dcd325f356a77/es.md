```
summary(io::IO, x)
str = summary(x)
```

Imprime en un flujo `io`, o devuelve una cadena `str`, dando una breve descripción de un valor. Por defecto, devuelve `string(typeof(x))`, por ejemplo, [`Int64`](@ref).

Para arreglos, devuelve una cadena con información sobre el tamaño y el tipo, por ejemplo, `10-element Array{Int64,1}`.

# Ejemplos

```jldoctest
julia> summary(1)
"Int64"

julia> summary(zeros(2))
"2-element Vector{Float64}"
```
