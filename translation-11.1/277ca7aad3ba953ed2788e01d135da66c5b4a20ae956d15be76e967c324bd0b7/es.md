```
float(x)
```

Convierte un número o arreglo a un tipo de dato de punto flotante.

Véase también: [`complex`](@ref), [`oftype`](@ref), [`convert`](@ref).

# Ejemplos

```jldoctest
julia> float(1:1000)
1.0:1.0:1000.0

julia> float(typemax(Int32))
2.147483647e9
```
