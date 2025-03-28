```
opnorm(A::AbstractMatrix, p::Real=2)
```

Calcula la norma del operador (o norma de matriz) inducida por la norma vectorial `p`, donde los valores válidos de `p` son `1`, `2` o `Inf`. (Ten en cuenta que para matrices dispersas, `p=2` actualmente no está implementado). Usa [`norm`](@ref) para calcular la norma de Frobenius.

Cuando `p=1`, la norma del operador es la suma máxima de columnas absolutas de `A`:

$$
\|A\|_1 = \max_{1 ≤ j ≤ n} \sum_{i=1}^m | a_{ij} |
$$

con $a_{ij}$ las entradas de $A$, y $m$ y $n$ sus dimensiones.

Cuando `p=2`, la norma del operador es la norma espectral, igual al mayor valor singular de `A`.

Cuando `p=Inf`, la norma del operador es la suma máxima de filas absolutas de `A`:

$$
\|A\|_\infty = \max_{1 ≤ i ≤ m} \sum _{j=1}^n | a_{ij} |
$$

# Ejemplos

```jldoctest
julia> A = [1 -2 -3; 2 3 -1]
2×3 Matrix{Int64}:
 1  -2  -3
 2   3  -1

julia> opnorm(A, Inf)
6.0

julia> opnorm(A, 1)
5.0
```
