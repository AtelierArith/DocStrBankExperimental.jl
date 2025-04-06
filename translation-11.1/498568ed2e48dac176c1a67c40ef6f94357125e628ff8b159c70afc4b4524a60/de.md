```
setindex!(A, X, inds...)
A[inds...] = X
```

Speichern Sie Werte aus dem Array `X` innerhalb einer Teilmenge von `A`, wie durch `inds` angegeben. Die Syntax `A[inds...] = X` ist äquivalent zu `(setindex!(A, X, inds...); X)`.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.


# Beispiele

```jldoctest
julia> A = zeros(2,2);

julia> setindex!(A, [10, 20], [1, 2]);

julia> A[[3, 4]] = [30, 40];

julia> A
2×2 Matrix{Float64}:
 10.0  30.0
 20.0  40.0
```
