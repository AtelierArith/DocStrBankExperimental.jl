```
skipmissing(itr)
```

Devuelve un iterador sobre los elementos en `itr` omitiendo los valores [`missing`](@ref). El objeto devuelto se puede indexar utilizando los índices de `itr` si este último es indexable. Los índices correspondientes a valores faltantes no son válidos: son omitidos por [`keys`](@ref) y [`eachindex`](@ref), y se lanza una `MissingException` al intentar usarlos.

Utiliza [`collect`](@ref) para obtener un `Array` que contenga los valores no `missing` en `itr`. Ten en cuenta que incluso si `itr` es un array multidimensional, el resultado siempre será un `Vector` ya que no es posible eliminar los valores faltantes mientras se preservan las dimensiones de la entrada.

Consulta también [`coalesce`](@ref), [`ismissing`](@ref), [`something`](@ref).

# Ejemplos

```jldoctest
julia> x = skipmissing([1, missing, 2])
skipmissing(Union{Missing, Int64}[1, missing, 2])

julia> sum(x)
3

julia> x[1]
1

julia> x[2]
ERROR: MissingException: el valor en el índice (2,) está faltando
[...]

julia> argmax(x)
3

julia> collect(keys(x))
Vector{Int64} de 2 elementos:
 1
 3

julia> collect(skipmissing([1, missing, 2]))
Vector{Int64} de 2 elementos:
 1
 2

julia> collect(skipmissing([1 missing; 2 missing]))
Vector{Int64} de 2 elementos:
 1
 2
```
