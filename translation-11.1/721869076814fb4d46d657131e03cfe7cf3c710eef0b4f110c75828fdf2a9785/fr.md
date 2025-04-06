```
mul!(C, A, B, α, β) -> C
```

Multiplication-addition de matrices ou de vecteurs en place combinée $A B α + C β$. Le résultat est stocké dans `C` en le remplaçant. Notez que `C` ne doit pas être aliasé avec `A` ou `B`.

!!! compat "Julia 1.3"
    `mul!` à cinq arguments nécessite au moins Julia 1.3.


# Exemples

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; C = [1.0 2.0; 3.0 4.0];

julia> α, β = 100.0, 10.0;

julia> mul!(C, A, B, α, β) === C
true

julia> C
2×2 Matrix{Float64}:
 310.0  320.0
 730.0  740.0

julia> C_original = [1.0 2.0; 3.0 4.0]; # Une copie de la valeur originale de C

julia> C == A * B * α + C_original * β
true
```
