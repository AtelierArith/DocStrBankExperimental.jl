```
sprandn([rng][,Type],m[,n],p::AbstractFloat)
```

Crea un vector disperso aleatorio de longitud `m` o una matriz dispersa de tamaño `m` por `n` con la probabilidad (independiente) especificada `p` de que cualquier entrada sea diferente de cero, donde los valores diferentes de cero se muestrean de la distribución normal. El argumento opcional `rng` especifica un generador de números aleatorios, consulta [Random Numbers](@ref).

!!! compat "Julia 1.1"
    Especificar el tipo de elemento de salida `Type` requiere al menos Julia 1.1.


# Ejemplos

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> sprandn(2, 2, 0.75)
2×2 SparseMatrixCSC{Float64, Int64} con 3 entradas almacenadas:
 -1.20577     ⋅
  0.311817  -0.234641
```
