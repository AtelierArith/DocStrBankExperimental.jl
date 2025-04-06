```
quantile(itr, p; sorted=false, alpha::Real=1.0, beta::Real=alpha)
```

Calcule les quantiles d'une collection `itr` à une probabilité spécifiée ou un vecteur ou un tuple de probabilités `p` sur l'intervalle [0,1]. L'argument clé `sorted` indique si `itr` peut être supposé trié.

Les quantiles d'échantillon sont définis par `Q(p) = (1-γ)*x[j] + γ*x[j+1]`, où `x[j]` est le j-ème ordre statistique de `itr`, `j = floor(n*p + m)`, `m = alpha + p*(1 - alpha - beta)` et `γ = n*p + m - j`.

Par défaut (`alpha = beta = 1`), les quantiles sont calculés par interpolation linéaire entre les points `((k-1)/(n-1), x[k])`, pour `k = 1:n` où `n = length(itr)`. Cela correspond à la Définition 7 de Hyndman et Fan (1996), et est le même que le défaut de R et NumPy.

Les arguments clés `alpha` et `beta` correspondent aux mêmes paramètres dans Hyndman et Fan, les définir à des valeurs différentes permet de calculer des quantiles avec n'importe laquelle des méthodes 4-9 définies dans cet article :

  * Def. 4 : `alpha=0`, `beta=1`
  * Def. 5 : `alpha=0.5`, `beta=0.5` (défaut MATLAB)
  * Def. 6 : `alpha=0`, `beta=0` (Excel `PERCENTILE.EXC`, défaut Python, Stata `altdef`)
  * Def. 7 : `alpha=1`, `beta=1` (défaut Julia, R et NumPy, Excel `PERCENTILE` et `PERCENTILE.INC`, Python `'inclusive'`)
  * Def. 8 : `alpha=1/3`, `beta=1/3`
  * Def. 9 : `alpha=3/8`, `beta=3/8`

!!! note
    Une `ArgumentError` est levée si `v` contient des valeurs `NaN` ou [`missing`](@ref). Utilisez la fonction [`skipmissing`](@ref) pour omettre les entrées `missing` et calculer les quantiles des valeurs non manquantes.


# Références

  * Hyndman, R.J et Fan, Y. (1996) "Sample Quantiles in Statistical Packages", *The American Statistician*, Vol. 50, No. 4, pp. 361-365
  * [Quantile sur Wikipedia](https://en.m.wikipedia.org/wiki/Quantile) détaille les différentes définitions de quantiles

# Exemples

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
