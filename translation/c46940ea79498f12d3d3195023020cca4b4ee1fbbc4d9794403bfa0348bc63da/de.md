```
sortslices(A; dims, alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Sortiere Scheiben eines Arrays `A`. Das erforderliche Schlüsselwortargument `dims` muss entweder eine ganze Zahl oder ein Tupel von ganzen Zahlen sein. Es gibt die Dimension(en) an, über die die Scheiben sortiert werden.

Zum Beispiel, wenn `A` eine Matrix ist, wird `dims=1` die Zeilen sortieren, `dims=2` wird die Spalten sortieren. Beachte, dass die Standardvergleichsfunktion für eindimensionale Scheiben lexikographisch sortiert.

Für die verbleibenden Schlüsselwortargumente siehe die Dokumentation von [`sort!`](@ref).

# Beispiele

```jldoctest
julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1) # Zeilen sortieren
3×3 Matrix{Int64}:
 -1   6  4
  7   3  5
  9  -2  8

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, rev=true)
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2) # Spalten sortieren
3×3 Matrix{Int64}:
  3   5  7
 -1  -4  6
 -2   8  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, alg=InsertionSort, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  5   3  7
 -4  -1  6
  8  -2  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, rev=true)
3×3 Matrix{Int64}:
 7   5   3
 6  -4  -1
 9   8  -2
```

# Höhere Dimensionen

`sortslices` erweitert sich natürlich auf höhere Dimensionen. Zum Beispiel, wenn `A` ein 2x2x2 Array ist, wird `sortslices(A, dims=3)` die Scheiben innerhalb der 3. Dimension sortieren, indem die 2x2 Scheiben `A[:, :, 1]` und `A[:, :, 2]` an die Vergleichsfunktion übergeben werden. Beachte, dass es für höherdimensionale Scheiben keine Standardreihenfolge gibt, du kannst jedoch das Schlüsselwortargument `by` oder `lt` verwenden, um eine solche Reihenfolge anzugeben.

Wenn `dims` ein Tupel ist, ist die Reihenfolge der Dimensionen in `dims` relevant und gibt die lineare Reihenfolge der Scheiben an. Zum Beispiel, wenn `A` dreidimensional ist und `dims` `(1, 2)` ist, werden die Anordnungen der ersten beiden Dimensionen so umgeordnet, dass die Scheiben (der verbleibenden dritten Dimension) sortiert werden. Wenn `dims` stattdessen `(2, 1)` ist, werden die gleichen Scheiben genommen, aber die Ergebnisreihenfolge wird zeilenweise sein.

# Beispiele für höhere Dimensionen

```
julia> A = [4 3; 2 1 ;;; 'A' 'B'; 'C' 'D']
2×2×2 Array{Any, 3}:
[:, :, 1] =
 4  3
 2  1

[:, :, 2] =
 'A'  'B'
 'C'  'D'

julia> sortslices(A, dims=(1,2))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 'D'  'B'
 'C'  'A'

julia> sortslices(A, dims=(2,1))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 'D'  'C'
 'B'  'A'

julia> sortslices(reshape([5; 4; 3; 2; 1], (1,1,5)), dims=3, by=x->x[1,1])
1×1×5 Array{Int64, 3}:
[:, :, 1] =
 1

[:, :, 2] =
 2

[:, :, 3] =
 3

[:, :, 4] =
 4

[:, :, 5] =
 5
```
