```
@evalpoly(z, c...)
```

Bewerten Sie das Polynom $\sum_k z^{k-1} c[k]$ für die Koeffizienten `c[1]`, `c[2]`, ...; das heißt, die Koeffizienten sind in aufsteigender Reihenfolge nach der Potenz von `z` angegeben. Dieses Makro erweitert sich zu effizientem Inline-Code, der entweder die Horner-Methode oder, für komplexe `z`, einen effizienteren Goertzel-ähnlichen Algorithmus verwendet.

Siehe auch [`evalpoly`](@ref).

# Beispiele

```jldoctest
julia> @evalpoly(3, 1, 0, 1)
10

julia> @evalpoly(2, 1, 0, 1)
5

julia> @evalpoly(2, 1, 1, 1)
7
```
