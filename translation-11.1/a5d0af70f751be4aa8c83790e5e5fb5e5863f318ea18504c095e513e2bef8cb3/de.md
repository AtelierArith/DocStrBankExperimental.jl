```
nullspace(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
nullspace(M, rtol::Real) = nullspace(M; rtol=rtol) # wird in Julia 2.0 veraltet sein

Berechnet eine Basis für den Nullraum von `M`, indem die singulären Vektoren von `M` einbezogen werden, deren singulären Werte Beträge kleiner als `max(atol, rtol*σ₁)` haben, wobei `σ₁` der größte singuläre Wert von `M` ist.

Standardmäßig ist die relative Toleranz `rtol` `n*ϵ`, wobei `n` die Größe der kleinsten Dimension von `M` ist und `ϵ` die [`eps`](@ref) des Elementtyps von `M`.

# Beispiele

```

jldoctest julia> M = [1 0 0; 0 1 0; 0 0 0] 3×3 Matrix{Int64}:  1  0  0  0  1  0  0  0  0

julia> nullspace(M) 3×1 Matrix{Float64}:  0.0  0.0  1.0

julia> nullspace(M, rtol=3) 3×3 Matrix{Float64}:  0.0  1.0  0.0  1.0  0.0  0.0  0.0  0.0  1.0

julia> nullspace(M, atol=0.95) 3×1 Matrix{Float64}:  0.0  0.0  1.0 ```
