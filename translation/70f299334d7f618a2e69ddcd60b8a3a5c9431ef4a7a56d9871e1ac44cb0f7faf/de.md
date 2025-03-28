```
Union{Typen...}
```

Ein `Union`-Typ ist ein abstrakter Typ, der alle Instanzen seiner Argumenttypen umfasst. Das bedeutet, dass `T <: Union{T,S}` und `S <: Union{T,S}`.

Wie andere abstrakte Typen kann er nicht instanziiert werden, selbst wenn alle seine Argumente nicht abstrakt sind.

# Beispiele

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 isa IntOrString # Instanz von Int ist im Union enthalten
true

julia> "Hello!" isa IntOrString # String ist ebenfalls enthalten
true

julia> 1.0 isa IntOrString # Float64 ist nicht enthalten, da es weder Int noch AbstractString ist
false
```

# Erweiterte Hilfe

Im Gegensatz zu den meisten anderen parametrischen Typen sind Unions in ihren Parametern kovariant. Zum Beispiel ist `Union{Real, String}` ein Subtyp von `Union{Number, AbstractString}`.

Die leere Union [`Union{}`](@ref) ist der unterste Typ von Julia.
