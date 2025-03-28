```
eachindex(A...)
eachindex(::IndexStyle, A::AbstractArray...)
```

Crea un objeto iterable para visitar cada índice de un `AbstractArray` `A` de manera eficiente. Para los tipos de arreglo que han optado por la indexación lineal rápida (como `Array`), esto es simplemente el rango `1:length(A)` si utilizan indexación basada en 1. Para los tipos de arreglo que no han optado por la indexación lineal rápida, generalmente se devuelve un rango cartesiano especializado para indexar eficientemente en el arreglo con índices especificados para cada dimensión.

En general, `eachindex` acepta iterables arbitrarios, incluidos cadenas y diccionarios, y devuelve un objeto iterador que admite tipos de índice arbitrarios (por ejemplo, índices desiguales o índices no enteros).

Si `A` es `AbstractArray`, es posible especificar explícitamente el estilo de los índices que deben ser devueltos por `eachindex` pasando un valor de tipo `IndexStyle` como su primer argumento (típicamente `IndexLinear()` si se requieren índices lineales o `IndexCartesian()` si se desea un rango cartesiano).

Si proporcionas más de un argumento `AbstractArray`, `eachindex` creará un objeto iterable que es rápido para todos los argumentos (típicamente un [`UnitRange`](@ref) si todas las entradas tienen indexación lineal rápida, un [`CartesianIndices`](@ref) de lo contrario). Si los arreglos tienen diferentes tamaños y/o dimensionalidades, se lanzará una excepción `DimensionMismatch`.

Consulta también [`pairs`](@ref)`(A)` para iterar sobre índices y valores juntos, y [`axes`](@ref)`(A, 2)` para índices válidos a lo largo de una dimensión.

# Ejemplos

```jldoctest
julia> A = [10 20; 30 40];

julia> for i in eachindex(A) # indexación lineal
           println("A[", i, "] == ", A[i])
       end
A[1] == 10
A[2] == 30
A[3] == 20
A[4] == 40

julia> for i in eachindex(view(A, 1:2, 1:1)) # indexación cartesiana
           println(i)
       end
CartesianIndex(1, 1)
CartesianIndex(2, 1)
```
