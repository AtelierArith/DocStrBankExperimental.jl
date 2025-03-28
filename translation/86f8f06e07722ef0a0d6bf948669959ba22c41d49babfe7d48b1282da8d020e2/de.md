```
argmax(f, domain)
```

Gibt einen Wert `x` aus `domain` zurück, für den `f(x)` maximiert wird. Wenn es mehrere maximale Werte für `f(x)` gibt, wird der erste gefunden.

`domain` muss eine nicht leere Iterable sein.

Werte werden mit `isless` verglichen.

!!! compat "Julia 1.7"
    Diese Methode erfordert Julia 1.7 oder höher.


Siehe auch [`argmin`](@ref), [`findmax`](@ref).

# Beispiele

```jldoctest
julia> argmax(abs, -10:5)
-10

julia> argmax(cos, 0:π/2:2π)
0.0
```
