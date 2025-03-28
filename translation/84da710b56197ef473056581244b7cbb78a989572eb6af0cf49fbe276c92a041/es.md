```
LinRange{T,L}
```

Un rango con `len` elementos espaciados linealmente entre su `start` y `stop`. El tamaño del espaciado está controlado por `len`, que debe ser un `Integer`.

# Ejemplos

```jldoctest
julia> LinRange(1.5, 5.5, 9)
9-element LinRange{Float64, Int64}:
 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5, 5.0, 5.5
```

En comparación con el uso de [`range`](@ref), construir directamente un `LinRange` debería tener menos sobrecarga pero no intentará corregir errores de punto flotante:

```jldoctest
julia> collect(range(-0.1, 0.3, length=5))
5-element Vector{Float64}:
 -0.1
  0.0
  0.1
  0.2
  0.3

julia> collect(LinRange(-0.1, 0.3, 5))
5-element Vector{Float64}:
 -0.1
 -1.3877787807814457e-17
  0.09999999999999999
  0.19999999999999998
  0.3
```

Consulta también [`Logrange`](@ref Base.LogRange) para puntos espaciados logarítmicamente.
