```
CartesianIndices(sz::Dims) -> R
CartesianIndices((istart:[istep:]istop, jstart:[jstep:]jstop, ...)) -> R
```

Define una región `R` que abarca un rango rectangular multidimensional de índices enteros. Estos se encuentran más comúnmente en el contexto de la iteración, donde `for I in R ... end` devolverá índices `I` equivalentes a los bucles anidados de [`CartesianIndex`](@ref)

```
for j = jstart:jstep:jstop
    for i = istart:istep:istop
        ...
    end
end
```

En consecuencia, estos pueden ser útiles para escribir algoritmos que funcionen en dimensiones arbitrarias.

```
CartesianIndices(A::AbstractArray) -> R
```

Como conveniencia, construir un `CartesianIndices` a partir de un array crea un rango de sus índices.

!!! compat "Julia 1.6"
    El método de rango de paso `CartesianIndices((istart:istep:istop, jstart:[jstep:]jstop, ...))` requiere al menos Julia 1.6.


# Ejemplos

```jldoctest
julia> foreach(println, CartesianIndices((2, 2, 2)))
CartesianIndex(1, 1, 1)
CartesianIndex(2, 1, 1)
CartesianIndex(1, 2, 1)
CartesianIndex(2, 2, 1)
CartesianIndex(1, 1, 2)
CartesianIndex(2, 1, 2)
CartesianIndex(1, 2, 2)
CartesianIndex(2, 2, 2)

julia> CartesianIndices(fill(1, (2,3)))
CartesianIndices((2, 3))
```

## Conversión entre índices lineales y cartesianas

La conversión de índice lineal a índice cartesiano explota el hecho de que un `CartesianIndices` es un `AbstractArray` y se puede indexar linealmente:

```jldoctest
julia> cartesian = CartesianIndices((1:3, 1:2))
CartesianIndices((1:3, 1:2))

julia> cartesian[4]
CartesianIndex(1, 2)

julia> cartesian = CartesianIndices((1:2:5, 1:2))
CartesianIndices((1:2:5, 1:2))

julia> cartesian[2, 2]
CartesianIndex(3, 2)
```

## Difusión

`CartesianIndices` soporta la aritmética de difusión (+ y -) con un `CartesianIndex`.

!!! compat "Julia 1.1"
    La difusión de CartesianIndices requiere al menos Julia 1.1.


```jldoctest
julia> CIs = CartesianIndices((2:3, 5:6))
CartesianIndices((2:3, 5:6))

julia> CI = CartesianIndex(3, 4)
CartesianIndex(3, 4)

julia> CIs .+ CI
CartesianIndices((5:6, 9:10))
```

Para la conversión de cartesian a índice lineal, consulta [`LinearIndices`](@ref). ```
