```
struct
```

El tipo más comúnmente utilizado en Julia es un struct, especificado como un nombre y un conjunto de campos.

```julia
struct Point
    x
    y
end
```

Los campos pueden tener restricciones de tipo, que pueden ser parametrizadas:

```julia
struct Point{X}
    x::X
    y::Float64
end
```

Un struct también puede declarar un supertipo abstracto a través de la sintaxis `<:`:

```julia
struct Point <: AbstractPoint
    x
    y
end
```

Los `struct`s son inmutables por defecto; una instancia de uno de estos tipos no puede ser modificada después de su construcción. Usa [`mutable struct`](@ref) en su lugar para declarar un tipo cuyas instancias pueden ser modificadas.

Consulta la sección del manual sobre [Tipos Compuestos](@ref) para más detalles, como cómo definir constructores.
