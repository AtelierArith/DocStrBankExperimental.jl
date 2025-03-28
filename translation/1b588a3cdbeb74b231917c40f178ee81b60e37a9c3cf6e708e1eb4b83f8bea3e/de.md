```
Funktion
```

Abstrakter Typ aller Funktionen.

# Beispiele

```jldoctest
julia> isa(+, Funktion)
true

julia> typeof(sin)
typeof(sin) (Singleton-Typ der Funktion sin, Untertyp von Funktion)

julia> ans <: Funktion
true
```
