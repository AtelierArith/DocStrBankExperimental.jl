```
@view A[inds...]
```

Transforma la expresión de indexación `A[inds...]` en la llamada equivalente a [`view`](@ref).

Esto solo se puede aplicar directamente a una única expresión de indexación y es particularmente útil para expresiones que incluyen las sintaxis de indexación especiales `begin` o `end` como `A[begin, 2:end-1]` (ya que no son compatibles con la función normal [`view`](@ref)).

Ten en cuenta que `@view` no se puede usar como el objetivo de una asignación regular (por ejemplo, `@view(A[1, 2:end]) = ...`), ni la [asignación indexada](@ref man-indexed-assignment) sin decorar (`A[1, 2:end] = ...`) o la asignación indexada transmitida (`A[1, 2:end] .= ...`) harían una copia. Sin embargo, puede ser útil para *actualizar* asignaciones transmitidas como `@view(A[1, 2:end]) .+= 1` porque esta es una sintaxis simple para `@view(A[1, 2:end]) .= @view(A[1, 2:end]) + 1`, y la expresión de indexación en el lado derecho de lo contrario haría una copia sin el `@view`.

Consulta también [`@views`](@ref) para cambiar un bloque completo de código para usar vistas para indexación no escalar.

!!! compat "Julia 1.5"
    Usar `begin` en una expresión de indexación para referirse al primer índice requiere al menos Julia 1.5.


# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = @view A[:, 1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A
2×2 Matrix{Int64}:
 0  2
 0  4
```
