```
ScopedValue(x)
```

Erstellen Sie einen Container, der Werte über dynamische Scopes hinweg propagiert. Verwenden Sie [`with`](@ref), um einen neuen dynamischen Scope zu erstellen und zu betreten.

Werte können nur beim Betreten eines neuen dynamischen Scopes gesetzt werden, und der referenzierte Wert bleibt während der Ausführung eines dynamischen Scopes konstant.

Dynamische Scopes werden über Aufgaben hinweg propagiert.

# Beispiele

```jldoctest
julia> using Base.ScopedValues;

julia> const sval = ScopedValue(1);

julia> sval[]
1

julia> with(sval => 2) do
           sval[]
       end
2

julia> sval[]
1
```

!!! compat "Julia 1.11"
    Scoped values wurden in Julia 1.11 eingeführt. In Julia 1.8+ ist eine kompatible Implementierung im Paket ScopedValues.jl verfügbar.

