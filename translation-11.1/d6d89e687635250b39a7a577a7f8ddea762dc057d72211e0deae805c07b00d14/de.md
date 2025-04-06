```
asum(n, X, incx)
```

Summe der Beträge der ersten `n` Elemente des Arrays `X` mit Schrittweite `incx`.

Für ein reelles Array ist der Betrag der absolute Wert. Für ein komplexes Array ist der Betrag die Summe des absoluten Wertes des Realteils und des absoluten Wertes des Imaginärteils.

# Beispiele

```jldoctest
julia> BLAS.asum(5, fill(1.0im, 10), 2)
5.0

julia> BLAS.asum(2, fill(1.0im, 10), 5)
2.0
```
