```
kron(A, B)
```

Berechnet das Kronecker-Produkt von zwei Vektoren, Matrizen oder Zahlen.

Für reelle Vektoren `v` und `w` steht das Kronecker-Produkt in Beziehung zum äußeren Produkt durch `kron(v,w) == vec(w * transpose(v))` oder `w * transpose(v) == reshape(kron(v,w), (length(w), length(v)))`. Beachten Sie, wie die Anordnung von `v` und `w` links und rechts dieser Ausdrücke unterschiedlich ist (aufgrund der spaltenweisen Speicherung). Bei komplexen Vektoren unterscheidet sich das äußere Produkt `w * v'` ebenfalls durch die Konjugation von `v`.

# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> B = [im 1; 1 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  1+0im
 1+0im  0-1im

julia> kron(A, B)
4×4 Matrix{Complex{Int64}}:
 0+1im  1+0im  0+2im  2+0im
 1+0im  0-1im  2+0im  0-2im
 0+3im  3+0im  0+4im  4+0im
 3+0im  0-3im  4+0im  0-4im

julia> v = [1, 2]; w = [3, 4, 5];

julia> w*transpose(v)
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10

julia> reshape(kron(v,w), (length(w), length(v)))
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10
```
