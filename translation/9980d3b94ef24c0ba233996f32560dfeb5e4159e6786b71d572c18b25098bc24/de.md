```
axes(A, d)
```

Gibt den gültigen Bereich der Indizes für das Array `A` entlang der Dimension `d` zurück.

Siehe auch [`size`](@ref) und das Handbuchkapitel über [Arrays mit benutzerdefinierten Indizes](@ref man-custom-indices).

# Beispiele

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A, 2)
Base.OneTo(6)

julia> axes(A, 4) == 1:1  # alle Dimensionen d > ndims(A) haben die Größe 1
true
```

# Verwendungshinweis

Jeder der Indizes muss ein `AbstractUnitRange{<:Integer}` sein, kann aber gleichzeitig ein Typ sein, der benutzerdefinierte Indizes verwendet. Wenn Sie beispielsweise eine Teilmenge benötigen, verwenden Sie verallgemeinerte Indexierungs-Konstrukte wie `begin`/`end` oder [`firstindex`](@ref)/[`lastindex`](@ref):

```julia
ix = axes(v, 1)
ix[2:end]          # funktioniert z.B. für Vector, kann aber allgemein fehlschlagen
ix[(begin+1):end]  # funktioniert für verallgemeinerte Indizes
```
