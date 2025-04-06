```
nullspace(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
nullspace(M, rtol::Real) = nullspace(M; rtol=rtol) # será desaprobado en Julia 2.0

Calcula una base para el espacio nulo de `M` incluyendo los vectores singulares de `M` cuyos valores singulares tienen magnitudes menores que `max(atol, rtol*σ₁)`, donde `σ₁` es el mayor valor singular de `M`.

Por defecto, la tolerancia relativa `rtol` es `n*ϵ`, donde `n` es el tamaño de la dimensión más pequeña de `M`, y `ϵ` es el [`eps`](@ref) del tipo de elemento de `M`.

# Ejemplos

```

jldoctest julia> M = [1 0 0; 0 1 0; 0 0 0] 3×3 Matrix{Int64}:  1  0  0  0  1  0  0  0  0

julia> nullspace(M) 3×1 Matrix{Float64}:  0.0  0.0  1.0

julia> nullspace(M, rtol=3) 3×3 Matrix{Float64}:  0.0  1.0  0.0  1.0  0.0  0.0  0.0  0.0  1.0

julia> nullspace(M, atol=0.95) 3×1 Matrix{Float64}:  0.0  0.0  1.0 ```
