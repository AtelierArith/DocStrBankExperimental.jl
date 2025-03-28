```
permutedims!(dest, src, perm)
```

Permutieren Sie die Dimensionen des Arrays `src` und speichern Sie das Ergebnis im Array `dest`. `perm` ist ein Vektor, der eine Permutation der Länge `ndims(src)` angibt. Das vorab zugewiesene Array `dest` sollte `size(dest) == size(src)[perm]` haben und wird vollständig überschrieben. Es wird keine In-Place-Permutation unterstützt, und unerwartete Ergebnisse treten auf, wenn `src` und `dest` überlappende Speicherbereiche haben.

Siehe auch [`permutedims`](@ref).
