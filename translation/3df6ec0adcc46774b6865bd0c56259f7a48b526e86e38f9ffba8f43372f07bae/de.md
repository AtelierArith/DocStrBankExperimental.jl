```
quantile(itr, p; sorted=false, alpha::Real=1.0, beta::Real=alpha)
```

Berechnen Sie das(e) Quantil(e) einer Sammlung `itr` bei einer angegebenen Wahrscheinlichkeit oder einem Vektor oder Tupel von Wahrscheinlichkeiten `p` im Intervall [0,1]. Das Schlüsselwortargument `sorted` gibt an, ob `itr` als sortiert angenommen werden kann.

Die Stichprobenquantile werden definiert durch `Q(p) = (1-γ)*x[j] + γ*x[j+1]`, wobei `x[j]` die j-te Ordnungsstatistik von `itr` ist, `j = floor(n*p + m)`, `m = alpha + p*(1 - alpha - beta)` und `γ = n*p + m - j`.

Standardmäßig (`alpha = beta = 1`) werden Quantile durch lineare Interpolation zwischen den Punkten `((k-1)/(n-1), x[k])` berechnet, für `k = 1:n`, wobei `n = length(itr)`. Dies entspricht Definition 7 von Hyndman und Fan (1996) und ist dasselbe wie das Standardverhalten von R und NumPy.

Die Schlüsselwortargumente `alpha` und `beta` entsprechen denselben Parametern in Hyndman und Fan; sie auf unterschiedliche Werte zu setzen, ermöglicht die Berechnung von Quantilen mit einer der Methoden 4-9, die in diesem Papier definiert sind:

  * Def. 4: `alpha=0`, `beta=1`
  * Def. 5: `alpha=0.5`, `beta=0.5` (MATLAB-Standard)
  * Def. 6: `alpha=0`, `beta=0` (Excel `PERCENTILE.EXC`, Python-Standard, Stata `altdef`)
  * Def. 7: `alpha=1`, `beta=1` (Julia, R und NumPy-Standard, Excel `PERCENTILE` und `PERCENTILE.INC`, Python `'inclusive'`)
  * Def. 8: `alpha=1/3`, `beta=1/3`
  * Def. 9: `alpha=3/8`, `beta=3/8`

!!! note
    Ein `ArgumentError` wird ausgelöst, wenn `v` `NaN` oder [`missing`](@ref) Werte enthält. Verwenden Sie die Funktion [`skipmissing`](@ref), um `missing`-Einträge zu überspringen und die Quantile der nicht fehlenden Werte zu berechnen.


# Referenzen

  * Hyndman, R.J und Fan, Y. (1996) "Sample Quantiles in Statistical Packages", *The American Statistician*, Vol. 50, No. 4, S. 361-365
  * [Quantile auf Wikipedia](https://en.m.wikipedia.org/wiki/Quantile) beschreibt die verschiedenen Quantildefinitionen

# Beispiele

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
