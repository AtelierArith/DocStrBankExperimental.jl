```
randexp([rng=default_rng()], [T=Float64], [dims...])
```

Genera un número aleatorio del tipo `T` de acuerdo con la distribución exponencial con escala 1. Opcionalmente, genera un arreglo de tales números aleatorios. El módulo `Base` actualmente proporciona una implementación para los tipos [`Float16`](@ref), [`Float32`](@ref) y [`Float64`](@ref) (el predeterminado).

# Ejemplos

```jldoctest
julia> rng = Xoshiro(123);

julia> randexp(rng, Float32)
1.1757717f0

julia> randexp(rng, 3, 3)
3×3 Matrix{Float64}:
 1.37766  0.456653  0.236418
 3.40007  0.229917  0.0684921
 0.48096  0.577481  0.71835
```
