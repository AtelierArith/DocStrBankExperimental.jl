```
+(x, y...)
```

Operador de adición.

La infija `x+y+z+...` llama a esta función con todos los argumentos, es decir, `+(x, y, z, ...)`, que por defecto luego llama a `(x+y) + z + ...` comenzando desde la izquierda.

Ten en cuenta que el desbordamiento es posible para la mayoría de los tipos de enteros, incluido el `Int` por defecto, al sumar números grandes.

# Ejemplos

```jldoctest
julia> 1 + 20 + 4
25

julia> +(1, 20, 4)
25

julia> [1,2] + [3,4]
2-element Vector{Int64}:
 4
 6

julia> typemax(Int) + 1 < 0
true
```
