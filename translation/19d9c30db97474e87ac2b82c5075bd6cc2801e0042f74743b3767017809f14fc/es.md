```
rdiv!(A, B)
```

Calcula `A / B` en su lugar y sobrescribiendo `A` para almacenar el resultado.

El argumento `B` *no* debe ser una matriz. En su lugar, debe ser un objeto de factorización (por ejemplo, producido por [`factorize`](@ref) o [`cholesky`](@ref)). La razón de esto es que la factorización en sí misma es costosa y típicamente asigna memoria (aunque también se puede hacer en su lugar a través de, por ejemplo, [`lu!`](@ref)), y las situaciones críticas de rendimiento que requieren `rdiv!` generalmente también requieren un control detallado sobre la factorización de `B`.

!!! note
    Ciertos tipos de matrices estructuradas, como `Diagonal` y `UpperTriangular`, están permitidos, ya que ya están en una forma factorizada.

