```
permutedims(v::AbstractVector)
```

Formatiere den Vektor `v` in eine `1 × length(v)` Zeilenmatrix um. Unterscheidet sich von [`transpose`](@ref) darin, dass die Operation nicht rekursiv ist, was besonders nützlich für Arrays mit nicht-numerischen Werten ist (wo das rekursive `transpose` einen Fehler auslösen könnte).

# Beispiele

Im Gegensatz zu `transpose` kann `permutedims` auf Vektoren beliebiger nicht-numerischer Elemente angewendet werden, wie z.B. Strings:

```jldoctest
julia> permutedims(["a", "b", "c"])
1×3 Matrix{String}:
 "a"  "b"  "c"
```

Für Vektoren von Zahlen funktioniert `permutedims(v)` ähnlich wie `transpose(v)`, mit dem Unterschied, dass der Rückgabetyp anders ist (es verwendet [`reshape`](@ref) anstelle einer `LinearAlgebra.Transpose`-Ansicht, obwohl beide den Speicher mit dem ursprünglichen Array `v` teilen):

```jldoctest; setup = :(using LinearAlgebra)
julia> v = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> p = permutedims(v)
1×4 Matrix{Int64}:
 1  2  3  4

julia> r = transpose(v)
1×4 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3  4

julia> p == r
true

julia> typeof(r)
Transpose{Int64, Vector{Int64}}

julia> p[1] = 5; r[2] = 6; # Mutieren von p oder r ändert auch v

julia> v # teilt den Speicher mit sowohl p als auch r
4-element Vector{Int64}:
 5
 6
 3
 4
```

Allerdings liefert `permutedims` Ergebnisse, die sich von `transpose` für Vektoren unterscheiden, deren Elemente selbst numerische Matrizen sind:

```jldoctest; setup = :(using LinearAlgebra)
julia> V = [[[1 2; 3 4]]; [[5 6; 7 8]]]
2-element Vector{Matrix{Int64}}:
 [1 2; 3 4]
 [5 6; 7 8]

julia> permutedims(V)
1×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [5 6; 7 8]

julia> transpose(V)
1×2 transpose(::Vector{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [5 7; 6 8]
```
