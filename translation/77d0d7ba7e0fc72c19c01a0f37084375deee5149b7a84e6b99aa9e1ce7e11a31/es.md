```
mutable struct
```

`mutable struct` es similar a [`struct`](@ref), pero además permite que los campos del tipo se establezcan después de la construcción.

Los campos individuales de un `mutable struct` pueden ser marcados como `const` para hacerlos inmutables:

```julia
mutable struct Baz
    a::Int
    const b::Float64
end
```

!!! compat "Julia 1.8"
    La palabra clave `const` para los campos de los `mutable structs` requiere al menos Julia 1.8.


Consulta la sección del manual sobre [Composite Types](@ref) para más información.
