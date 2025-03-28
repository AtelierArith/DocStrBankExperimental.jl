```
LinRange{T,L}
```

Une plage avec `len` éléments espacés linéairement entre son `start` et `stop`. La taille de l'espacement est contrôlée par `len`, qui doit être un `Integer`.

# Exemples

```jldoctest
julia> LinRange(1.5, 5.5, 9)
9-element LinRange{Float64, Int64}:
 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5, 5.0, 5.5
```

Comparé à l'utilisation de [`range`](@ref), la construction directe d'un `LinRange` devrait avoir moins de surcharge mais ne tentera pas de corriger les erreurs de point flottant :

```jldoctest
julia> collect(range(-0.1, 0.3, length=5))
5-element Vector{Float64}:
 -0.1
  0.0
  0.1
  0.2
  0.3

julia> collect(LinRange(-0.1, 0.3, 5))
5-element Vector{Float64}:
 -0.1
 -1.3877787807814457e-17
  0.09999999999999999
  0.19999999999999998
  0.3
```

Voir aussi [`Logrange`](@ref Base.LogRange) pour des points espacés logarithmiquement.
