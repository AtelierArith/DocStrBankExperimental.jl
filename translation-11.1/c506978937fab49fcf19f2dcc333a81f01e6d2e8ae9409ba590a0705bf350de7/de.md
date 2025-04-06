```
argmin(f, domain)
```

Gibt einen Wert `x` aus `domain` zurück, für den `f(x)` minimiert wird. Wenn es mehrere minimale Werte für `f(x)` gibt, wird der erste gefunden.

`domain` muss eine nicht leere Iterable sein.

`NaN` wird als kleiner als alle anderen Werte außer `missing` behandelt.

!!! compat "Julia 1.7"
    Diese Methode erfordert Julia 1.7 oder später.


Siehe auch [`argmax`](@ref), [`findmin`](@ref).

# Beispiele

```jldoctest
julia> argmin(sign, -10:5)
-10

julia> argmin(x -> -x^3 + x^2 - 10, -5:5)
5

julia> argmin(acos, 0:0.1:1)
1.0
```
