```
quantile(itr, p; sorted=false, alpha::Real=1.0, beta::Real=alpha)
```

Calcula el(los) cuantil(es) de una colección `itr` en una probabilidad especificada o vector o tupla de probabilidades `p` en el intervalo [0,1]. El argumento clave `sorted` indica si se puede asumir que `itr` está ordenado.

Los cuantiles de muestra se definen por `Q(p) = (1-γ)*x[j] + γ*x[j+1]`, donde `x[j]` es la j-ésima estadística de orden de `itr`, `j = floor(n*p + m)`, `m = alpha + p*(1 - alpha - beta)` y `γ = n*p + m - j`.

Por defecto (`alpha = beta = 1`), los cuantiles se calculan mediante interpolación lineal entre los puntos `((k-1)/(n-1), x[k])`, para `k = 1:n` donde `n = length(itr)`. Esto corresponde a la Definición 7 de Hyndman y Fan (1996), y es el mismo que el valor predeterminado de R y NumPy.

Los argumentos clave `alpha` y `beta` corresponden a los mismos parámetros en Hyndman y Fan, establecerlos en diferentes valores permite calcular cuantiles con cualquiera de los métodos 4-9 definidos en este documento:

  * Def. 4: `alpha=0`, `beta=1`
  * Def. 5: `alpha=0.5`, `beta=0.5` (valor predeterminado de MATLAB)
  * Def. 6: `alpha=0`, `beta=0` (Excel `PERCENTILE.EXC`, valor predeterminado de Python, Stata `altdef`)
  * Def. 7: `alpha=1`, `beta=1` (valor predeterminado de Julia, R y NumPy, Excel `PERCENTILE` y `PERCENTILE.INC`, Python `'inclusive'`)
  * Def. 8: `alpha=1/3`, `beta=1/3`
  * Def. 9: `alpha=3/8`, `beta=3/8`

!!! note
    Se lanza un `ArgumentError` si `v` contiene valores `NaN` o [`missing`](@ref). Usa la función [`skipmissing`](@ref) para omitir entradas `missing` y calcular los cuantiles de los valores no faltantes.


# Referencias

  * Hyndman, R.J y Fan, Y. (1996) "Sample Quantiles in Statistical Packages", *The American Statistician*, Vol. 50, No. 4, pp. 361-365
  * [Quantile en Wikipedia](https://en.m.wikipedia.org/wiki/Quantile) detalla las diferentes definiciones de cuantil

# Ejemplos

```jldoctest
julia> using Statistics

julia> quantile(0:20, 0.5)
10.0

julia> quantile(0:20, [0.1, 0.5, 0.9])
3-element Vector{Float64}:
  2.0
 10.0
 18.000000000000004

julia> quantile(skipmissing([1, 10, missing]), 0.5)
5.5
```
