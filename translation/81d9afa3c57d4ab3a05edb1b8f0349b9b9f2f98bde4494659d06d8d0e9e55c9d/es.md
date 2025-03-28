```
ScopedValue(x)
```

Crea un contenedor que propaga valores a través de ámbitos dinámicos. Usa [`with`](@ref) para crear y entrar en un nuevo ámbito dinámico.

Los valores solo se pueden establecer al entrar en un nuevo ámbito dinámico, y el valor al que se hace referencia será constante durante la ejecución de un ámbito dinámico.

Los ámbitos dinámicos se propagan a través de tareas.

# Ejemplos

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
    Los valores escopados se introdujeron en Julia 1.11. En Julia 1.8+ una implementación compatible está disponible desde el paquete ScopedValues.jl.

