```
normalize(a, p::Real=2)
```

Normaliser `a` de sorte que sa `p`-norme soit égale à l'unité, c'est-à-dire `norm(a, p) == 1`. Pour les scalaires, cela est similaire à sign(a), sauf que normalize(0) = NaN. Voir aussi [`normalize!`](@ref), [`norm`](@ref), et [`sign`](@ref).

# Exemples

```jldoctest
julia> a = [1,2,4];

julia> b = normalize(a)
3-element Vector{Float64}:
 0.2182178902359924
 0.4364357804719848
 0.8728715609439696

julia> norm(b)
1.0

julia> c = normalize(a, 1)
3-element Vector{Float64}:
 0.14285714285714285
 0.2857142857142857
 0.5714285714285714

julia> norm(c, 1)
1.0

julia> a = [1 2 4 ; 1 2 4]
2×3 Matrix{Int64}:
 1  2  4
 1  2  4

julia> norm(a)
6.48074069840786

julia> normalize(a)
2×3 Matrix{Float64}:
 0.154303  0.308607  0.617213
 0.154303  0.308607  0.617213

julia> normalize(3, 1)
1.0

julia> normalize(-8, 1)
-1.0

julia> normalize(0, 1)
NaN
```
