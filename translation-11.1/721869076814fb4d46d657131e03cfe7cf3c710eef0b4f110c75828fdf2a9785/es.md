```
mul!(C, A, B, α, β) -> C
```

Multiplicación y suma de matrices o de matriz-vectores en su lugar combinada $A B α + C β$. El resultado se almacena en `C` sobrescribiéndolo. Tenga en cuenta que `C` no debe estar aliasado con `A` o `B`.

!!! compat "Julia 1.3"
    `mul!` de cinco argumentos requiere al menos Julia 1.3.


# Ejemplos

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; C = [1.0 2.0; 3.0 4.0];

julia> α, β = 100.0, 10.0;

julia> mul!(C, A, B, α, β) === C
true

julia> C
2×2 Matrix{Float64}:
 310.0  320.0
 730.0  740.0

julia> C_original = [1.0 2.0; 3.0 4.0]; # Una copia del valor original de C

julia> C == A * B * α + C_original * β
true
```
