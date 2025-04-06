```
evalpoly(x, p)
```

Evalúa el polinomio $\sum_k x^{k-1} p[k]$ para los coeficientes `p[1]`, `p[2]`, ...; es decir, los coeficientes se dan en orden ascendente por potencia de `x`. Los bucles se desenrollan en tiempo de compilación si el número de coeficientes se conoce estáticamente, es decir, cuando `p` es un `Tuple`. Esta función genera código eficiente utilizando el método de Horner si `x` es real, o utilizando un algoritmo similar a Goertzel [^DK62] si `x` es complejo.

[^DK62]: Donald Knuth, Art of Computer Programming, Volume 2: Seminumerical Algorithms, Sec. 4.6.4.

!!! compat "Julia 1.4"
    Esta función requiere Julia 1.4 o posterior.


# Ejemplos

```jldoctest
julia> evalpoly(2, (1, 2, 3))
17
```
