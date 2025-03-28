```
svd(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD
```

Calcula la descomposición en valores singulares (SVD) de `A` y devuelve un objeto `SVD`.

`U`, `S`, `V` y `Vt` se pueden obtener de la factorización `F` con `F.U`, `F.S`, `F.V` y `F.Vt`, de tal manera que `A = U * Diagonal(S) * Vt`. El algoritmo produce `Vt` y, por lo tanto, es más eficiente extraer `Vt` que `V`. Los valores singulares en `S` están ordenados en orden descendente.

Iterar la descomposición produce los componentes `U`, `S` y `V`.

Si `full = false` (por defecto), se devuelve una SVD "delgada". Para una matriz `A` de $M \times N$, en la factorización completa `U` es $M \times M$ y `V` es $N \times N$, mientras que en la factorización delgada `U` es $M \times K$ y `V` es $N \times K$, donde $K = \min(M,N)$ es el número de valores singulares.

Si `alg = DivideAndConquer()`, se utiliza un algoritmo de divide y vencerás para calcular la SVD. Otra opción (típicamente más lenta pero más precisa) es `alg = QRIteration()`.

!!! compat "Julia 1.3"
    El argumento de palabra clave `alg` requiere Julia 1.3 o posterior.


# Ejemplos

```jldoctest
julia> A = rand(4,3);

julia> F = svd(A); # Almacenar el objeto de factorización

julia> A ≈ F.U * Diagonal(F.S) * F.Vt
true

julia> U, S, V = F; # desestructuración a través de la iteración

julia> A ≈ U * Diagonal(S) * V'
true

julia> Uonly, = svd(A); # Almacenar solo U

julia> Uonly == U
true
```
