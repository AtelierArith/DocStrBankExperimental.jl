```
LogRange{T}(start, stop, len) <: AbstractVector{T}
```

Une plage dont les éléments sont espacés logarithmiquement entre `start` et `stop`, avec un espacement contrôlé par `len`. Renvoie par [`logrange`](@ref).

Comme [`LinRange`](@ref), les premier et dernier éléments seront exactement ceux fournis, mais les valeurs intermédiaires peuvent avoir de petites erreurs de flottement. Celles-ci sont calculées en utilisant les logarithmes des points d'extrémité, qui sont stockés lors de la construction, souvent avec une précision supérieure à `T`.

# Exemples

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

Notez que le type d'élément entier `T` n'est pas autorisé. Utilisez par exemple `round.(Int, xs)`, ou des puissances explicites d'une certaine base entière :

```jldoctest
julia> xs = logrange(1, 512, 4)
4-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 1.0, 8.0, 64.0, 512.0

julia> 2 .^ (0:3:9) |> println
[1, 8, 64, 512]
```

!!! compat "Julia 1.11"
    Ce type nécessite au moins Julia 1.11.

