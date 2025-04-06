```
LogRange{T}(start, stop, len) <: AbstractVector{T}
```

Un rango cuyos elementos están espaciados logarítmicamente entre `start` y `stop`, con el espaciado controlado por `len`. Devuelto por [`logrange`](@ref).

Al igual que [`LinRange`](@ref), los primeros y últimos elementos serán exactamente los proporcionados, pero los valores intermedios pueden tener pequeños errores de punto flotante. Estos se calculan utilizando los logaritmos de los puntos finales, que se almacenan en la construcción, a menudo en una precisión mayor que `T`.

# Ejemplos

```jldoctest
julia> logrange(1, 4, length=5)
5-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 1.0, 1.41421, 2.0, 2.82843, 4.0

julia> Base.LogRange{Float16}(1, 4, 5)
5-element Base.LogRange{Float16, Float64}:
 1.0, 1.414, 2.0, 2.828, 4.0

julia> logrange(1e-310, 1e-300, 11)[1:2:end]
6-element Vector{Float64}:
 1.0e-310
 9.999999999999974e-309
 9.999999999999981e-307
 9.999999999999988e-305
 9.999999999999994e-303
 1.0e-300

julia> prevfloat(1e-308, 5) == ans[2]
true
```

Tenga en cuenta que el tipo de eltype entero `T` no está permitido. Use, por ejemplo, `round.(Int, xs)`, o potencias explícitas de alguna base entera:

```jldoctest
julia> xs = logrange(1, 512, 4)
4-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 1.0, 8.0, 64.0, 512.0

julia> 2 .^ (0:3:9) |> println
[1, 8, 64, 512]
```

!!! compat "Julia 1.11"
    Este tipo requiere al menos Julia 1.11.

