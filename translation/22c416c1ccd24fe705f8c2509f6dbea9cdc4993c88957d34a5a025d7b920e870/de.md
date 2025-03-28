```
mod1(x, y)
```

Modulus nach ganzzahliger Division, gibt einen Wert `r` zurück, sodass `mod(r, y) == mod(x, y)` im Bereich $(0, y]$ für positives `y` und im Bereich $[y,0)$ für negatives `y`.

Bei ganzzahligen Argumenten und positivem `y` entspricht dies `mod(x, 1:y)`, und ist daher natürlich für 1-basierte Indizierung. Im Vergleich dazu ist `mod(x, y) == mod(x, 0:y-1)` natürlich für Berechnungen mit Offsets oder Schritten.

Siehe auch [`mod`](@ref), [`fld1`](@ref), [`fldmod1`](@ref).

# Beispiele

```jldoctest
julia> mod1(4, 2)
2

julia> mod1.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) mit eltype Int64:
 1  2  3  1  2  3  1  2  3  1  2

julia> mod1.([-0.1, 0, 0.1, 1, 2, 2.9, 3, 3.1]', 3)
1×8 Matrix{Float64}:
 2.9  3.0  0.1  1.0  2.0  2.9  3.0  0.1
```
