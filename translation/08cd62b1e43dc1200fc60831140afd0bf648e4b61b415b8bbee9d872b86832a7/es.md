```
sprand([rng],[T::Type],m,[n],p::AbstractFloat)
sprand([rng],m,[n],p::AbstractFloat,[rfn=rand])
```

Crea un vector disperso de longitud `m` o una matriz dispersa de `m` por `n`, en la que la probabilidad de que cualquier elemento sea diferente de cero se da de manera independiente por `p` (y, por lo tanto, la densidad media de elementos diferentes de cero también es exactamente `p`). El argumento opcional `rng` especifica un generador de números aleatorios, consulta [Números Aleatorios](@ref). El argumento opcional `T` especifica el tipo de elemento, que por defecto es `Float64`.

Por defecto, los valores diferentes de cero se muestrean de una distribución uniforme utilizando la función [`rand`](@ref), es decir, mediante `rand(T)`, o `rand(rng, T)` si se proporciona `rng`; para el `T=Float64` por defecto, esto corresponde a valores diferentes de cero muestreados uniformemente en `[0,1)`.

Puedes muestrear valores diferentes de cero de una distribución diferente pasando una función `rfn` personalizada en lugar de `rand`. Esta debe ser una función `rfn(k)` que devuelva un arreglo de `k` números aleatorios muestreados de la distribución deseada; alternativamente, si se proporciona `rng`, debería ser en su lugar una función `rfn(rng, k)`.

# Ejemplos

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> sprand(Bool, 2, 2, 0.5)
2×2 SparseMatrixCSC{Bool, Int64} con 2 entradas almacenadas:
 1  1
 ⋅  ⋅

julia> sprand(Float64, 3, 0.75)
Vector disperso de 3 elementos{Float64, Int64} con 2 entradas almacenadas:
  [1]  =  0.795547
  [2]  =  0.49425
```
