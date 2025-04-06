```
summary(io::IO, x)
str = summary(x)
```

Druckt in einen Stream `io` oder gibt einen String `str` zurück, der eine kurze Beschreibung eines Wertes liefert. Standardmäßig wird `string(typeof(x))` zurückgegeben, z.B. [`Int64`](@ref).

Für Arrays wird ein String mit Größen- und Typinformationen zurückgegeben, z.B. `10-element Array{Int64,1}`.

# Beispiele

```jldoctest
julia> summary(1)
"Int64"

julia> summary(zeros(2))
"2-element Vector{Float64}"
```
