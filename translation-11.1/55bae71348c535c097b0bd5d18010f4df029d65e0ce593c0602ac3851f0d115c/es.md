```
hermitianpart!(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

Sobrescribe la matriz cuadrada `A` en su lugar con su parte hermitiana `(A + A') / 2`, y devuelve [`Hermitian(A, uplo)`](@ref). Para matrices reales `A`, esto también se conoce como la parte simétrica de `A`.

Consulta también [`hermitianpart`](@ref) para la operación correspondiente fuera de lugar.

!!! compat "Julia 1.10"
    Esta función requiere Julia 1.10 o posterior.

