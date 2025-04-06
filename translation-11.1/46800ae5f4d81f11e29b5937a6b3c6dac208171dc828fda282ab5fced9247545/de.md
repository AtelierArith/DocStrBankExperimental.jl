```
reinterpret(reshape, T, A::AbstractArray{S}) -> B
```

Ändert die Typinterpretation von `A`, während eine "Kanaldimension" hinzugefügt oder konsumiert wird.

Wenn `sizeof(T) = n*sizeof(S)` für `n>1`, muss die erste Dimension von `A` die Größe `n` haben und `B` fehlt die erste Dimension von `A`. Umgekehrt, wenn `sizeof(S) = n*sizeof(T)` für `n>1`, erhält `B` eine neue erste Dimension der Größe `n`. Die Dimensionalität bleibt unverändert, wenn `sizeof(T) == sizeof(S)`.

!!! compat "Julia 1.6"
    Diese Methode erfordert mindestens Julia 1.6.


# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reinterpret(reshape, Complex{Int}, A)    # das Ergebnis ist ein Vektor
2-element reinterpret(reshape, Complex{Int64}, ::Matrix{Int64}) with eltype Complex{Int64}:
 1 + 3im
 2 + 4im

julia> a = [(1,2,3), (4,5,6)]
2-element Vector{Tuple{Int64, Int64, Int64}}:
 (1, 2, 3)
 (4, 5, 6)

julia> reinterpret(reshape, Int, a)             # das Ergebnis ist eine Matrix
3×2 reinterpret(reshape, Int64, ::Vector{Tuple{Int64, Int64, Int64}}) with eltype Int64:
 1  4
 2  5
 3  6
```
