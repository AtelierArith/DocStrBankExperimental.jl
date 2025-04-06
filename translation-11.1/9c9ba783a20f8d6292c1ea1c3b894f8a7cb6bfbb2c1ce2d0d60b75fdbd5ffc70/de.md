```
quantile!([q::AbstractArray, ] v::AbstractVector, p; sorted=false, alpha::Real=1.0, beta::Real=alpha)
```

Berechnet das Quantil(e) eines Vektors `v` bei einer angegebenen Wahrscheinlichkeit oder einem Vektor oder Tupel von Wahrscheinlichkeiten `p` im Intervall [0,1]. Wenn `p` ein Vektor ist, kann auch ein optionales Ausgabearray `q` angegeben werden. (Wenn nicht bereitgestellt, wird ein neues Ausgabearray erstellt.) Das Schlüsselwortargument `sorted` gibt an, ob `v` als sortiert angenommen werden kann; wenn `false` (der Standard), werden die Elemente von `v` teilweise in-place sortiert.

Die Stichprobenquantile werden definiert durch `Q(p) = (1-γ)*x[j] + γ*x[j+1]`, wobei `x[j]` die j-te Ordnungsstatistik von `v` ist, `j = floor(n*p + m)`, `m = alpha + p*(1 - alpha - beta)` und `γ = n*p + m - j`.

Standardmäßig (`alpha = beta = 1`) werden Quantile durch lineare Interpolation zwischen den Punkten `((k-1)/(n-1), x[k])` berechnet, für `k = 1:n`, wobei `n = length(v)`. Dies entspricht Definition 7 von Hyndman und Fan (1996) und ist dasselbe wie der Standard in R und NumPy.

Die Schlüsselwortargumente `alpha` und `beta` entsprechen denselben Parametern in Hyndman und Fan; sie auf unterschiedliche Werte zu setzen, ermöglicht die Berechnung von Quantilen mit einer der Methoden 4-9, die in diesem Papier definiert sind:

  * Def. 4: `alpha=0`, `beta=1`
  * Def. 5: `alpha=0.5`, `beta=0.5` (MATLAB-Standard)
  * Def. 6: `alpha=0`, `beta=0` (Excel `PERCENTILE.EXC`, Python-Standard, Stata `altdef`)
  * Def. 7: `alpha=1`, `beta=1` (Julia, R und NumPy-Standard, Excel `PERCENTILE` und `PERCENTILE.INC`, Python `'inclusive'`)
  * Def. 8: `alpha=1/3`, `beta=1/3`
  * Def. 9: `alpha=3/8`, `beta=3/8`

!!! note
    Ein `ArgumentError` wird ausgelöst, wenn `v` `NaN` oder [`missing`](@ref) Werte enthält.


# Referenzen

  * Hyndman, R.J und Fan, Y. (1996) "Sample Quantiles in Statistical Packages", *The American Statistician*, Vol. 50, No. 4, S. 361-365
  * [Quantile auf Wikipedia](https://en.m.wikipedia.org/wiki/Quantile) beschreibt die verschiedenen Quantildefinitionen

# Beispiele

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
