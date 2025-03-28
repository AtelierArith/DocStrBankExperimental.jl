```
spdiagm(kv::Pair{<:Integer,<:AbstractVector}...)
spdiagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)

Konstruiere eine spärliche Diagonalmatrize aus `Pair`s von Vektoren und Diagonalen. Jeder Vektor `kv.second` wird auf der `kv.first` Diagonale platziert. Standardmäßig ist die Matrix quadratisch und ihre Größe wird aus `kv` abgeleitet, aber eine nicht-quadratische Größe `m`×`n` (mit Nullen aufgefüllt, falls erforderlich) kann angegeben werden, indem `m,n` als erste Argumente übergeben werden.

# Beispiele

```

jldoctest julia> spdiagm(-1 => [1,2,3,4], 1 => [4,3,2,1]) 5×5 SparseMatrixCSC{Int64, Int64} mit 8 gespeicherten Einträgen:  ⋅  4  ⋅  ⋅  ⋅  1  ⋅  3  ⋅  ⋅  ⋅  2  ⋅  2  ⋅  ⋅  ⋅  3  ⋅  1  ⋅  ⋅  ⋅  4  ⋅ ```
