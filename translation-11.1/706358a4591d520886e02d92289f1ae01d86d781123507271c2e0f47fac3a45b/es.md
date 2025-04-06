```
sqrt(A::AbstractMatrix)
```

Si `A` no tiene valores propios reales negativos, calcula la raíz cuadrada principal de la matriz `A`, es decir, la matriz única $X$ con valores propios que tienen parte real positiva tal que $X^2 = A$. De lo contrario, se devuelve una raíz cuadrada no principal.

Si `A` es simétrica real o hermítica, se utiliza su descomposición en valores propios ([`eigen`](@ref)) para calcular la raíz cuadrada. Para tales matrices, los valores propios λ que parecen ser ligeramente negativos debido a errores de redondeo se tratan como si fueran cero. Más precisamente, las matrices con todos los valores propios `≥ -rtol*(max |λ|)` se tratan como semidefinidas (produciendo una raíz cuadrada hermítica), con los valores propios negativos considerados como cero. `rtol` es un argumento de palabra clave para `sqrt` (solo en el caso hermítico/simétrico real) que por defecto es la precisión de la máquina escalada por `size(A,1)`.

De lo contrario, la raíz cuadrada se determina por medio del método de Björck-Hammarling [^BH83], que calcula la forma de Schur compleja ([`schur`](@ref)) y luego la raíz cuadrada compleja del factor triangular. Si existe una raíz cuadrada real, entonces se utiliza una extensión de este método [^H87] que calcula la forma de Schur real y luego la raíz cuadrada real del factor cuasi-triangular.

[^BH83]: Åke Björck y Sven Hammarling, "Un método de Schur para la raíz cuadrada de una matriz", Álgebra Lineal y sus Aplicaciones, 52-53, 1983, 127-140. [doi:10.1016/0024-3795(83)80010-X](https://doi.org/10.1016/0024-3795(83)80010-X)

[^H87]: Nicholas J. Higham, "Cálculo de raíces cuadradas reales de una matriz real", Álgebra Lineal y sus Aplicaciones, 88-89, 1987, 405-430. [doi:10.1016/0024-3795(87)90118-2](https://doi.org/10.1016/0024-3795(87)90118-2)

# Ejemplos

```jldoctest
julia> A = [4 0; 0 4]
2×2 Matrix{Int64}:
 4  0
 0  4

julia> sqrt(A)
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
