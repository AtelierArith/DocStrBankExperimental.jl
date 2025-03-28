```
mul!(Y, A, B) -> Y
```

Calcula el producto de matriz-matriz o matriz-vector $A B$ y almacena el resultado en `Y`, sobrescribiendo el valor existente de `Y`. Ten en cuenta que `Y` no debe estar aliasado con `A` o `B`.

# Ejemplos

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; Y = similar(B);

julia> mul!(Y, A, B) === Y
true

julia> Y
2×2 Matrix{Float64}:
 3.0  3.0
 7.0  7.0

julia> Y == A * B
true
```

# Implementación

Para tipos de matriz y vector personalizados, se recomienda implementar `mul!` de 5 argumentos en lugar de implementar directamente `mul!` de 3 argumentos si es posible.
