```
permute!(v, p)
```

Permutieren Sie den Vektor `v` in-place gemäß der Permutation `p`. Es wird keine Überprüfung durchgeführt, um zu verifizieren, dass `p` eine Permutation ist.

Um eine neue Permutation zurückzugeben, verwenden Sie `v[p]`. Dies ist im Allgemeinen schneller als `permute!(v, p)`; es ist sogar schneller, in ein vorab zugewiesenes Ausgabearray mit `u .= @view v[p]` zu schreiben. (Obwohl `permute!` `v` in-place überschreibt, erfordert es intern einige Zuweisungen, um nachzuhalten, welche Elemente verschoben wurden.)

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.


Siehe auch [`invpermute!`](@ref).

# Beispiele

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> permute!(A, perm);

julia> A
4-element Vector{Int64}:
 1
 4
 3
 1
```
