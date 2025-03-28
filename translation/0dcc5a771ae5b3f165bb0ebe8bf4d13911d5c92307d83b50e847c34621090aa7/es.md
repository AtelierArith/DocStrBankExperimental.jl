```
ldiv!(Y, A, B) -> Y
```

Calcula `A \ B` en su lugar y almacena el resultado en `Y`, devolviendo el resultado.

El argumento `A` no debe ser una matriz. En su lugar, debe ser un objeto de factorización (por ejemplo, producido por [`factorize`](@ref) o [`cholesky`](@ref)). La razón de esto es que la factorización en sí misma es costosa y típicamente asigna memoria (aunque también se puede hacer en su lugar a través de, por ejemplo, [`lu!`](@ref)), y las situaciones críticas de rendimiento que requieren `ldiv!` generalmente también requieren un control detallado sobre la factorización de `A`.

!!! nota
    Ciertos tipos de matrices estructuradas, como `Diagonal` y `UpperTriangular`, están permitidos, ya que ya están en una forma factorizada.


# Ejemplos

```jldoctest
julia> A = [1 2.2 4; 3.1 0.2 3; 4 1 2];

julia> X = [1; 2.5; 3];

julia> Y = zero(X);

julia> ldiv!(Y, qr(A), X);

julia> Y ≈ A\X
true
```
