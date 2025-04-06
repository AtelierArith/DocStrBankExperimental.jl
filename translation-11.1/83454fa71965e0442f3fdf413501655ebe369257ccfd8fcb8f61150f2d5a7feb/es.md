```
norm(A, p::Real=2)
```

Para cualquier contenedor iterable `A` (incluyendo arreglos de cualquier dimensión) de números (o cualquier tipo de elemento para el cual `norm` está definido), calcula la `p`-norma (por defecto `p=2`) como si `A` fuera un vector de la longitud correspondiente.

La `p`-norma se define como

$$
\|A\|_p = \left( \sum_{i=1}^n | a_i | ^p \right)^{1/p}
$$

con $a_i$ las entradas de `A`, $| a_i |$ la [`norm`](@ref) de $a_i$, y $n$ la longitud de `A`. Dado que la `p`-norma se calcula utilizando las [`norm`](@ref)s de las entradas de `A$, la`p`-norma de un vector de vectores no es compatible con la interpretación de este como un vector bloque en general si`p != 2`.

`p` puede asumir cualquier valor numérico (aunque no todos los valores producen una norma de vector matemáticamente válida). En particular, `norm(A, Inf)` devuelve el valor más grande en `abs.(A)`, mientras que `norm(A, -Inf)` devuelve el más pequeño. Si `A` es una matriz y `p=2`, entonces esto es equivalente a la norma de Frobenius.

El segundo argumento `p` no es necesariamente parte de la interfaz para `norm`, es decir, un tipo personalizado puede implementar solo `norm(A)` sin el segundo argumento.

Usa [`opnorm`](@ref) para calcular la norma del operador de una matriz.

# Ejemplos

```jldoctest
julia> v = [3, -2, 6]
3-element Vector{Int64}:
  3
 -2
  6

julia> norm(v)
7.0

julia> norm(v, 1)
11.0

julia> norm(v, Inf)
6.0

julia> norm([1 2 3; 4 5 6; 7 8 9])
16.881943016134134

julia> norm([1 2 3 4 5 6 7 8 9])
16.881943016134134

julia> norm(1:9)
16.881943016134134

julia> norm(hcat(v,v), 1) == norm(vcat(v,v), 1) != norm([v,v], 1)
true

julia> norm(hcat(v,v), 2) == norm(vcat(v,v), 2) == norm([v,v], 2)
true

julia> norm(hcat(v,v), Inf) == norm(vcat(v,v), Inf) != norm([v,v], Inf)
true
```
