```
invpermute!(v, p)
```

Wie [`permute!`](@ref), aber die Inverse der gegebenen Permutation wird angewendet.

Beachten Sie, dass es schneller ist, ein vorab zugewiesenes Ausgabearray zu verwenden (z. B. `u = similar(v)`), anstatt `u[p] = v` zu verwenden. (`invpermute!` allokiert intern eine Kopie der Daten.)

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.


# Beispiele

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> invpermute!(A, perm);

julia> A
4-element Vector{Int64}:
 4
 1
 3
 1
```
