```
view(A, inds...)
```

Como [`getindex`](@ref), pero devuelve un array ligero que referencia de manera perezosa (o es efectivamente una *vista* de) el array padre `A` en el índice o índices dados `inds` en lugar de extraer elementos de manera ansiosa o construir un subconjunto copiado. Llamar a [`getindex`](@ref) o [`setindex!`](@ref) en el valor devuelto (a menudo un [`SubArray`](@ref)) calcula los índices para acceder o modificar el array padre sobre la marcha. El comportamiento es indefinido si la forma del array padre cambia después de que se llama a `view` porque no hay verificación de límites para el array padre; por ejemplo, puede causar un fallo de segmentación.

Algunos arrays padres inmutables (como los rangos) pueden optar por simplemente recomputar un nuevo array en algunas circunstancias en lugar de devolver un `SubArray` si hacerlo es eficiente y proporciona semánticas compatibles.

!!! compat "Julia 1.6"
    En Julia 1.6 o posterior, `view` se puede llamar en un `AbstractString`, devolviendo un `SubString`.


# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = view(A, :, 1)
2-element view(::Matrix{Int64}, :, 1) con el tipo eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) con el tipo eltype Int64:
 0
 0

julia> A # Nota que A ha cambiado aunque modificamos b
2×2 Matrix{Int64}:
 0  2
 0  4

julia> view(2:5, 2:3) # devuelve un rango ya que el tipo es inmutable
3:4
```
