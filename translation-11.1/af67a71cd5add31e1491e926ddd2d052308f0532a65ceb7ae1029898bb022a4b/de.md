```
transpose!(dest,src)
```

Transponiere das Array `src` und speichere das Ergebnis im vorab allokierten Array `dest`, das eine Größe entsprechend `(size(src,2),size(src,1))` haben sollte. Es wird keine In-Place-Transposition unterstützt, und unerwartete Ergebnisse treten auf, wenn `src` und `dest` überlappende Speicherbereiche haben.

# Beispiele

```jldoctest
julia> A = [3+2im 9+2im; 8+7im  4+6im]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im

julia> B = zeros(Complex{Int64}, 2, 2)
2×2 Matrix{Complex{Int64}}:
 0+0im  0+0im
 0+0im  0+0im

julia> transpose!(B, A);

julia> B
2×2 Matrix{Complex{Int64}}:
 3+2im  8+7im
 9+2im  4+6im

julia> A
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im
```
