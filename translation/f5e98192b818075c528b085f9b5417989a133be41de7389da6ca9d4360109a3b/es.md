```
hermitianpart(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

Devuelve la parte hermitiana de la matriz cuadrada `A`, definida como `(A + A') / 2`, como una matriz [`Hermitian`](@ref). Para matrices reales `A`, esto también se conoce como la parte simétrica de `A`; a veces también se le llama la "parte real del operador". El argumento opcional `uplo` controla el argumento correspondiente de la vista [`Hermitian`](@ref). Para matrices reales, esta última es equivalente a una vista [`Symmetric`](@ref).

Véase también [`hermitianpart!`](@ref) para la operación correspondiente en su lugar.

!!! compat "Julia 1.10"
    Esta función requiere Julia 1.10 o posterior.

