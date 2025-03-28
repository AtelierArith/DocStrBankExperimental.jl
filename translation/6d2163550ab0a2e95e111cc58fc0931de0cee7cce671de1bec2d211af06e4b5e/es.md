```
Vararg{T,N}
```

El último parámetro de un tipo de tupla [`Tuple`](@ref) puede ser el valor especial `Vararg`, que denota cualquier número de elementos finales. `Vararg{T,N}` corresponde exactamente a `N` elementos del tipo `T`. Finalmente, `Vararg{T}` corresponde a cero o más elementos del tipo `T`. Los tipos de tupla `Vararg` se utilizan para representar los argumentos aceptados por los métodos de varargs (ver la sección sobre [Funciones Varargs](@ref) en el manual).

Véase también [`NTuple`](@ref).

# Ejemplos

```jldoctest
julia> mytupletype = Tuple{AbstractString, Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```
