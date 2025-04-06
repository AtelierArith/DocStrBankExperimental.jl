```
nfields(x) -> Int
```

Erhalte die Anzahl der Felder im gegebenen Objekt.

# Beispiele

```jldoctest
julia> a = 1//2;

julia> nfields(a)
2

julia> b = 1
1

julia> nfields(b)
0

julia> ex = ErrorException("Ich habe etwas Schlimmes getan");

julia> nfields(ex)
1
```

In diesen Beispielen ist `a` ein [`Rational`](@ref), das zwei Felder hat. `b` ist ein `Int`, das ein primitiver Bittyp ohne Felder ist. `ex` ist eine [`ErrorException`](@ref), die ein Feld hat.
