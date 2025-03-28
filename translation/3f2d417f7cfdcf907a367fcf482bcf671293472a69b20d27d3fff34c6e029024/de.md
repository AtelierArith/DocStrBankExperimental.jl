```
struct
```

Die am häufigsten verwendete Art von Typ in Julia ist ein struct, der als Name und eine Menge von Feldern angegeben wird.

```julia
struct Point
    x
    y
end
```

Felder können Typbeschränkungen haben, die parametrisiert sein können:

```julia
struct Point{X}
    x::X
    y::Float64
end
```

Ein struct kann auch einen abstrakten Supertyp über die `<:`-Syntax deklarieren:

```julia
struct Point <: AbstractPoint
    x
    y
end
```

`struct`s sind standardmäßig unveränderlich; eine Instanz eines dieser Typen kann nach der Konstruktion nicht mehr geändert werden. Verwenden Sie [`mutable struct`](@ref), um einen Typ zu deklarieren, dessen Instanzen geändert werden können.

Siehe den Handbuchabschnitt über [Composite Types](@ref) für weitere Details, wie z.B. wie man Konstruktoren definiert.
