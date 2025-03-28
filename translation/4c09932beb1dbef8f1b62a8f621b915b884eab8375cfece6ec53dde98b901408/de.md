```
diagm(kv::Pair{<:Integer,<:AbstractVector}...)
diagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)

Konstruiere eine Matrix aus `Pair`s von Diagonalen und Vektoren. Der Vektor `kv.second` wird auf der `kv.first` Diagonale platziert. Standardmäßig ist die Matrix quadratisch und ihre Größe wird aus `kv` abgeleitet, aber eine nicht-quadratische Größe `m`×`n` (mit Nullen aufgefüllt, falls nötig) kann angegeben werden, indem `m,n` als erste Argumente übergeben werden. Bei wiederholten diagonalen Indizes `kv.first` werden die Werte in den entsprechenden Vektoren `kv.second` addiert.

`diagm` konstruiert eine vollständige Matrix; wenn Sie speichereffiziente Versionen mit schneller Arithmetik wünschen, sehen Sie sich [`Diagonal`](@ref), [`Bidiagonal`](@ref), [`Tridiagonal`](@ref) und [`SymTridiagonal`](@ref) an.

# Beispiele

```

jldoctest julia> diagm(1 => [1,2,3]) 4×4 Matrix{Int64}:  0  1  0  0  0  0  2  0  0  0  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], -1 => [4,5]) 4×4 Matrix{Int64}:  0  1  0  0  4  0  2  0  0  5  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], 1 => [1,2,3]) 4×4 Matrix{Int64}:  0  2  0  0  0  0  4  0  0  0  0  6  0  0  0  0 ```
