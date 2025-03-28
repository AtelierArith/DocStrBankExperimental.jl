```
BoundsError([a],[i])
```

Une opération d'indexation dans un tableau, `a`, a tenté d'accéder à un élément hors limites à l'index `i`.

# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> A = fill(1.0, 7);

julia> A[8]
ERREUR : BoundsError : tentative d'accès à un Vector{Float64} de 7 éléments à l'index [8]


julia> B = fill(1.0, (2,3));

julia> B[2, 4]
ERREUR : BoundsError : tentative d'accès à un Matrix{Float64} de 2×3 à l'index [2, 4]


julia> B[9]
ERREUR : BoundsError : tentative d'accès à un Matrix{Float64} de 2×3 à l'index [9]

```
