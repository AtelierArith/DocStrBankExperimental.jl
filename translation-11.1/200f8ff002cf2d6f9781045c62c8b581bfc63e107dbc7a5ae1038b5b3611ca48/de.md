```
eigmin(A; permute::Bool=true, scale::Bool=true)
```

Gibt den kleinsten Eigenwert von `A` zurück. Die Option `permute=true` permutiert die Matrix, um näher an eine obere Dreiecksmatrix zu gelangen, und `scale=true` skaliert die Matrix nach ihren Diagonalelementen, um Zeilen und Spalten normgleichmäßiger zu machen. Beachten Sie, dass diese Methode fehlschlägt, wenn die Eigenwerte von `A` komplex sind, da komplexe Zahlen nicht sortiert werden können.

# Beispiele

```jldoctest
julia> A = [0 im; -im 0]
2×2 Matrix{Complex{Int64}}:
 0+0im  0+1im
 0-1im  0+0im

julia> eigmin(A)
-1.0

julia> A = [0 im; -1 0]
2×2 Matrix{Complex{Int64}}:
  0+0im  0+1im
 -1+0im  0+0im

julia> eigmin(A)
ERROR: DomainError with Complex{Int64}[0+0im 0+1im; -1+0im 0+0im]:
`A` kann keine komplexen Eigenwerte haben.
Stacktrace:
[...]
```
