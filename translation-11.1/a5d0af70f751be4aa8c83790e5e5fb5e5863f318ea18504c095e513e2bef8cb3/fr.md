```
nullspace(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
nullspace(M, rtol::Real) = nullspace(M; rtol=rtol) # à déprécier dans Julia 2.0

Calcule une base pour le noyau de `M` en incluant les vecteurs singuliers de `M` dont les valeurs singulières ont des magnitudes inférieures à `max(atol, rtol*σ₁)`, où `σ₁` est la plus grande valeur singulière de `M`.

Par défaut, la tolérance relative `rtol` est `n*ϵ`, où `n` est la taille de la plus petite dimension de `M`, et `ϵ` est le [`eps`](@ref) du type d'élément de `M`.

# Exemples

```

jldoctest julia> M = [1 0 0; 0 1 0; 0 0 0] 3×3 Matrix{Int64}:  1  0  0  0  1  0  0  0  0

julia> nullspace(M) 3×1 Matrix{Float64}:  0.0  0.0  1.0

julia> nullspace(M, rtol=3) 3×3 Matrix{Float64}:  0.0  1.0  0.0  1.0  0.0  0.0  0.0  0.0  1.0

julia> nullspace(M, atol=0.95) 3×1 Matrix{Float64}:  0.0  0.0  1.0 ```
