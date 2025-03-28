```
muladd(x, y, z)
```

Kombinierte Multiplikation-Addition: berechnet `x*y+z`, erlaubt jedoch, dass die Addition und Multiplikation mit einander oder mit umgebenden Operationen zur Leistungssteigerung zusammengeführt werden. Zum Beispiel kann dies als [`fma`](@ref) implementiert werden, wenn die Hardware dies effizient unterstützt. Das Ergebnis kann auf verschiedenen Maschinen unterschiedlich sein und kann auch auf derselben Maschine aufgrund von Konstantenpropagation oder anderen Optimierungen unterschiedlich sein. Siehe [`fma`](@ref).

# Beispiele

```jldoctest
julia> muladd(3, 2, 1)
7

julia> 3 * 2 + 1
7
```
