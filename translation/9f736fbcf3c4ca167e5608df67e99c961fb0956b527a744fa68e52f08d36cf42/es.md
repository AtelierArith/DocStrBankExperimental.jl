```
logrange(inicio, fin, longitud)
logrange(inicio, fin; longitud)
```

Construye un arreglo especializado cuyos elementos están espaciados logarítmicamente entre los puntos finales dados. Es decir, la razón de los elementos sucesivos es constante, calculada a partir de la longitud.

Esto es similar a `geomspace` en Python. A diferencia de `PowerRange` en Mathematica, especificas el número de elementos, no la razón. A diferencia de `logspace` en Python y Matlab, los argumentos `inicio` y `fin` son siempre el primer y último elemento del resultado, no potencias aplicadas a alguna base.

# Ejemplos

```jldoctest
julia> logrange(10, 4000, longitud=3)
3-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 10.0, 200.0, 4000.0

julia> ans[2] ≈ sqrt(10 * 4000)  # el elemento del medio es la media geométrica
true

julia> range(10, 40, longitud=3)[2] ≈ (10 + 40)/2  # media aritmética
true

julia> logrange(1f0, 32f0, 11)
11-element Base.LogRange{Float32, Float64}:
 1.0, 1.41421, 2.0, 2.82843, 4.0, 5.65685, 8.0, 11.3137, 16.0, 22.6274, 32.0

julia> logrange(1, 1000, longitud=4) ≈ 10 .^ (0:3)
true
```

Consulta el tipo [`LogRange`](@ref Base.LogRange) para más detalles.

Consulta también [`range`](@ref) para puntos espaciados linealmente.

!!! compat "Julia 1.11"
    Esta función requiere al menos Julia 1.11.

