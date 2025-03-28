```
//(num, den)
```

Teile zwei ganze Zahlen oder rationale Zahlen, wobei ein [`Rational`](@ref) Ergebnis zurückgegeben wird. Allgemeiner kann `//` für die exakte rationale Division anderer numerischer Typen mit ganzzahligen oder rationalen Komponenten verwendet werden, wie z. B. komplexe Zahlen mit ganzzahligen Komponenten.

Beachte, dass Gleitkomma-([`AbstractFloat`](@ref)) Argumente von `//` nicht erlaubt sind (auch wenn die Werte rational sind). Die Argumente müssen Untertypen von [`Integer`](@ref), `Rational` oder deren Kombinationen sein.

# Beispiele

```jldoctest
julia> 3 // 5
3//5

julia> (3 // 5) // (2 // 1)
3//10

julia> (1+2im) // (3+4im)
11//25 + 2//25*im

julia> 1.0 // 2
ERROR: MethodError: no method matching //(::Float64, ::Int64)
[...]
```
