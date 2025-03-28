```
clamp!(array::AbstractArray, lo, hi)
```

Restringe los valores en `array` al rango especificado, en su lugar. Ver también [`clamp`](@ref).

!!! compat "Julia 1.3"
    Las entradas `missing` en `array` requieren al menos Julia 1.3.


# Ejemplos

```jldoctest
julia> row = collect(-4:4)';

julia> clamp!(row, 0, Inf)
1×9 adjoint(::Vector{Int64}) con el tipo eltype Int64:
 0  0  0  0  0  1  2  3  4

julia> clamp.((-4:4)', 0, Inf)
1×9 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  1.0  2.0  3.0  4.0
```
