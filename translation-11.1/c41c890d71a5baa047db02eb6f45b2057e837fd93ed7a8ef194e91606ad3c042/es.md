```
randn([rng=default_rng()], [T=Float64], [dims...])
```

Genera un número aleatorio distribuido normalmente de tipo `T` con media 0 y desviación estándar 1. Dado el argumento opcional `dims`, genera un arreglo de tamaño `dims` de tales números. La biblioteca estándar de Julia soporta `randn` para cualquier tipo de punto flotante que implemente [`rand`](@ref), por ejemplo, los tipos de `Base` [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref) (el predeterminado) y [`BigFloat`](@ref), junto con sus contrapartes [`Complex`](@ref).

(Cuando `T` es complejo, los valores se extraen de la distribución normal compleja circularmente simétrica de varianza 1, correspondiente a partes real e imaginaria que tienen una distribución normal independiente con media cero y varianza `1/2`).

Consulta también [`randn!`](@ref) para actuar en su lugar.

# Ejemplos

Generando un solo número aleatorio (con el tipo predeterminado `Float64`):

```julia-repl
julia> randn()
-0.942481877315864
```

Generando una matriz de números aleatorios normales (con el tipo predeterminado `Float64`):

```julia-repl
julia> randn(2,3)
2×3 Matrix{Float64}:
  1.18786   -0.678616   1.49463
 -0.342792  -0.134299  -1.45005
```

Configurando el generador de números aleatorios `rng` con una semilla definida por el usuario (para números reproducibles) y usándolo para generar un número aleatorio `Float32` o una matriz de números aleatorios `ComplexF32`:

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> randn(rng, Float32)
-0.6457307f0

julia> randn(rng, ComplexF32, (2, 3))
2×3 Matrix{ComplexF32}:
  -1.03467-1.14806im  0.693657+0.056538im   0.291442+0.419454im
 -0.153912+0.34807im    1.0954-0.948661im  -0.543347-0.0538589im
```
