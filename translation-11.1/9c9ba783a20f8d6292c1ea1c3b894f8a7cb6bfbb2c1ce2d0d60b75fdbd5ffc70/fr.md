```
quantile!([q::AbstractArray, ] v::AbstractVector, p; sorted=false, alpha::Real=1.0, beta::Real=alpha)
```

Calcule le(s) quantile(s) d'un vecteur `v` à une probabilité spécifiée ou un vecteur ou un tuple de probabilités `p` sur l'intervalle [0,1]. Si `p` est un vecteur, un tableau de sortie optionnel `q` peut également être spécifié. (S'il n'est pas fourni, un nouveau tableau de sortie est créé.) L'argument clé `sorted` indique si `v` peut être supposé trié ; si `false` (par défaut), alors les éléments de `v` seront partiellement triés sur place.

Les quantiles d'échantillon sont définis par `Q(p) = (1-γ)*x[j] + γ*x[j+1]`, où `x[j]` est la j-ème statistique d'ordre de `v`, `j = floor(n*p + m)`, `m = alpha + p*(1 - alpha - beta)` et `γ = n*p + m - j`.

Par défaut (`alpha = beta = 1`), les quantiles sont calculés par interpolation linéaire entre les points `((k-1)/(n-1), x[k])`, pour `k = 1:n` où `n = length(v)`. Cela correspond à la Définition 7 de Hyndman et Fan (1996), et est le même que le défaut de R et NumPy.

Les arguments clés `alpha` et `beta` correspondent aux mêmes paramètres dans Hyndman et Fan, les définir à des valeurs différentes permet de calculer des quantiles avec n'importe laquelle des méthodes 4-9 définies dans cet article :

  * Def. 4 : `alpha=0`, `beta=1`
  * Def. 5 : `alpha=0.5`, `beta=0.5` (défaut MATLAB)
  * Def. 6 : `alpha=0`, `beta=0` (Excel `PERCENTILE.EXC`, défaut Python, Stata `altdef`)
  * Def. 7 : `alpha=1`, `beta=1` (défaut Julia, R et NumPy, Excel `PERCENTILE` et `PERCENTILE.INC`, Python `'inclusive'`)
  * Def. 8 : `alpha=1/3`, `beta=1/3`
  * Def. 9 : `alpha=3/8`, `beta=3/8`

!!! note
    Une `ArgumentError` est levée si `v` contient des valeurs `NaN` ou [`missing`](@ref).


# Références

  * Hyndman, R.J et Fan, Y. (1996) "Sample Quantiles in Statistical Packages", *The American Statistician*, Vol. 50, No. 4, pp. 361-365
  * [Quantile sur Wikipedia](https://en.m.wikipedia.org/wiki/Quantile) détaille les différentes définitions de quantile

# Exemples

```jldoctest
julia> using Statistics

julia> x = [3, 2, 1];

julia> quantile!(x, 0.5)
2.0

julia> x
3-element Vector{Int64}:
 1
 2
 3

julia> y = zeros(3);

julia> quantile!(y, x, [0.1, 0.5, 0.9]) === y
true

julia> y
3-element Vector{Float64}:
 1.2000000000000002
 2.0
 2.8000000000000003
```
