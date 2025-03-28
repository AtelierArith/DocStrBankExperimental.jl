```
only(x)
```

Gibt das einzige Element der Sammlung `x` zurück oder wirft einen [`ArgumentError`](@ref), wenn die Sammlung null oder mehrere Elemente hat.

Siehe auch [`first`](@ref), [`last`](@ref).

!!! compat "Julia 1.4"
    Diese Methode erfordert mindestens Julia 1.4.


# Beispiele

```jldoctest
julia> only(["a"])
"a"

julia> only("a")
'a': ASCII/Unicode U+0061 (Kategorie Ll: Kleinbuchstabe)

julia> only(())
ERROR: ArgumentError: Tuple enthält 0 Elemente, muss genau 1 Element enthalten
Stacktrace:
[...]

julia> only(('a', 'b'))
ERROR: ArgumentError: Tuple enthält 2 Elemente, muss genau 1 Element enthalten
Stacktrace:
[...]
```
