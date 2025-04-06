```
Iterators.map(f, iterators...)
```

Erstellen Sie eine faule Zuordnung. Dies ist eine andere Syntax, um `(f(args...) for args in zip(iterators...))` zu schreiben.

!!! compat "Julia 1.6"
    Diese Funktion erfordert mindestens Julia 1.6.


# Beispiele

```jldoctest
julia> collect(Iterators.map(x -> x^2, 1:3))
3-element Vector{Int64}:
 1
 4
 9
```
