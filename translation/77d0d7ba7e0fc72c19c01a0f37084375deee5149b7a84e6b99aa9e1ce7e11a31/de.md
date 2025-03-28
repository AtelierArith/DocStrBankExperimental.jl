```
mutable struct
```

`mutable struct` ist ähnlich wie [`struct`](@ref), erlaubt jedoch zusätzlich, dass die Felder des Typs nach der Konstruktion gesetzt werden.

Einzelne Felder eines `mutable struct` können als `const` markiert werden, um sie unveränderlich zu machen:

```julia
mutable struct Baz
    a::Int
    const b::Float64
end
```

!!! compat "Julia 1.8"
    Das `const`-Schlüsselwort für Felder von `mutable structs` erfordert mindestens Julia 1.8.


Siehe den Handbuchabschnitt über [Composite Types](@ref) für weitere Informationen.
