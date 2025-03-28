```
Diagonal(V::AbstractVector)
```

Construye una matriz perezosa con `V` como su diagonal.

Véase también [`UniformScaling`](@ref) para la matriz identidad perezosa `I`, [`diagm`](@ref) para hacer una matriz densa, y [`diag`](@ref) para extraer elementos diagonales.

# Ejemplos

```jldoctest
julia> d = Diagonal([1, 10, 100])
3×3 Diagonal{Int64, Vector{Int64}}:
 1   ⋅    ⋅
 ⋅  10    ⋅
 ⋅   ⋅  100

julia> diagm([7, 13])
2×2 Matrix{Int64}:
 7   0
 0  13

julia> ans + I
2×2 Matrix{Int64}:
 8   0
 0  14

julia> I(2)
2×2 Diagonal{Bool, Vector{Bool}}:
 1  ⋅
 ⋅  1
```

!!! nota
    Una matriz de una columna no se trata como un vector, sino que llama al método `Diagonal(A::AbstractMatrix)` que extrae `diag(A)` de 1 elemento:


```jldoctest
julia> A = transpose([7.0 13.0])
2×1 transpose(::Matrix{Float64}) con el tipo de elemento Float64:
  7.0
 13.0

julia> Diagonal(A)
1×1 Diagonal{Float64, Vector{Float64}}:
 7.0
```
