```
gcdx(a, b)
```

Calcula el máximo común divisor (positivo) de `a` y `b` y sus coeficientes de Bézout, es decir, los coeficientes enteros `u` y `v` que satisfacen $ua+vb = d = gcd(a, b)$. `gcdx(a, b)` devuelve $(d, u, v)$.

Los argumentos pueden ser números enteros y racionales.

!!! compat "Julia 1.4"
    Los argumentos racionales requieren Julia 1.4 o posterior.


# Ejemplos

```jldoctest
julia> gcdx(12, 42)
(6, -3, 1)

julia> gcdx(240, 46)
(2, -9, 47)
```

!!! note
    Los coeficientes de Bézout *no* están definidos de manera única. `gcdx` devuelve los coeficientes de Bézout mínimos que se calculan mediante el algoritmo de Euclides extendido. (Ref: D. Knuth, TAoCP, 2/e, p. 325, Algoritmo X.) Para enteros firmados, estos coeficientes `u` y `v` son mínimos en el sentido de que $|u| < |b/d|$ y $|v| < |a/d|$. Además, los signos de `u` y `v` se eligen de modo que `d` sea positivo. Para enteros no firmados, los coeficientes `u` y `v` pueden estar cerca de su `typemax`, y la identidad solo se mantiene a través de la aritmética modular de los enteros no firmados.

