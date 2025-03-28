```
map(f, A::AbstractArray...) -> N-array
```

Al actuar sobre arreglos multidimensionales del mismo [`ndims`](@ref), todos deben tener los mismos [`axes`](@ref), y la respuesta también lo tendrá.

Véase también [`broadcast`](@ref), que permite tamaños desiguales.

# Ejemplos

```
julia> map(//, [1 2; 3 4], [4 3; 2 1])
2×2 Matrix{Rational{Int64}}:
 1//4  2//3
 3//2  4//1

julia> map(+, [1 2; 3 4], zeros(2,1))
ERROR: DimensionMismatch

julia> map(+, [1 2; 3 4], [1,10,100,1000], zeros(3,1))  # itera hasta que el 3º se agote
3-element Vector{Float64}:
   2.0
  13.0
 102.0
```
