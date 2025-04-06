```
eachslice(A::AbstractArray; dims, drop=true)
```

Crea un objeto [`Slices`](@ref) que es un arreglo de cortes sobre las dimensiones `dims` de `A`, devolviendo vistas que seleccionan todos los datos de las otras dimensiones en `A`. `dims` puede ser un entero o una tupla de enteros.

Si `drop = true` (el valor predeterminado), el `Slices` externo eliminará las dimensiones internas, y el orden de las dimensiones coincidirá con las de `dims`. Si `drop = false`, entonces el `Slices` tendrá la misma dimensionalidad que el arreglo subyacente, con dimensiones internas de tamaño 1.

Consulta [`stack`](@ref)`(slices; dims)` para la inversa de `eachslice(A; dims::Integer)`.

También consulta [`eachrow`](@ref), [`eachcol`](@ref), [`mapslices`](@ref) y [`selectdim`](@ref).

!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1.


!!! compat "Julia 1.9"
    Antes de Julia 1.9, esto devolvía un iterador, y solo se soportaba una única dimensión `dims`.


# Ejemplos

```jldoctest
julia> m = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> s = eachslice(m, dims=1)
3-element RowSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]

julia> s[1]
3-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2
 3

julia> eachslice(m, dims=1, drop=false)
3×1 Slices{Matrix{Int64}, Tuple{Int64, Colon}, Tuple{Base.OneTo{Int64}, Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}, 2}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]
```
