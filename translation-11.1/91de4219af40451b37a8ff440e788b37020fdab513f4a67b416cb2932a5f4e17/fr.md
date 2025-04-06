```
map(f, A::AbstractArray...) -> N-array
```

Lorsqu'il agit sur des tableaux multidimensionnels de la même [`ndims`](@ref), ils doivent tous avoir les mêmes [`axes`](@ref), et la réponse le sera aussi.

Voir aussi [`broadcast`](@ref), qui permet des tailles non correspondantes.

# Exemples

```
julia> map(//, [1 2; 3 4], [4 3; 2 1])
2×2 Matrix{Rational{Int64}}:
 1//4  2//3
 3//2  4//1

julia> map(+, [1 2; 3 4], zeros(2,1))
ERROR: DimensionMismatch

julia> map(+, [1 2; 3 4], [1,10,100,1000], zeros(3,1))  # itère jusqu'à ce que le 3ème soit épuisé
3-element Vector{Float64}:
   2.0
  13.0
 102.0
```
