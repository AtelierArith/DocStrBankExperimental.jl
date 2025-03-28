```
@evalpoly(z, c...)
```

Evalúa el polinomio $\sum_k z^{k-1} c[k]$ para los coeficientes `c[1]`, `c[2]`, ...; es decir, los coeficientes se dan en orden ascendente por potencia de `z`. Este macro se expande a código en línea eficiente que utiliza ya sea el método de Horner o, para `z` complejos, un algoritmo más eficiente similar al de Goertzel.

Véase también [`evalpoly`](@ref).

# Ejemplos

```jldoctest
julia> @evalpoly(3, 1, 0, 1)
10

julia> @evalpoly(2, 1, 0, 1)
5

julia> @evalpoly(2, 1, 1, 1)
7
```
