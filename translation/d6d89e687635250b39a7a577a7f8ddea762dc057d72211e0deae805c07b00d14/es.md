```
asum(n, X, incx)
```

Suma de las magnitudes de los primeros `n` elementos del arreglo `X` con paso `incx`.

Para un arreglo real, la magnitud es el valor absoluto. Para un arreglo complejo, la magnitud es la suma del valor absoluto de la parte real y el valor absoluto de la parte imaginaria.

# Ejemplos

```jldoctest
julia> BLAS.asum(5, fill(1.0im, 10), 2)
5.0

julia> BLAS.asum(2, fill(1.0im, 10), 5)
2.0
```
