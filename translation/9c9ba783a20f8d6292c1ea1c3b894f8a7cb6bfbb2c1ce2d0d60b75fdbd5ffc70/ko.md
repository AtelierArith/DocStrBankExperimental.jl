```
quantile!([q::AbstractArray, ] v::AbstractVector, p; sorted=false, alpha::Real=1.0, beta::Real=alpha)
```

벡터 `v`의 분위수를 지정된 확률 또는 확률의 벡터 또는 튜플 `p`에 대해 [0,1] 구간에서 계산합니다. `p`가 벡터인 경우, 선택적으로 출력 배열 `q`를 지정할 수 있습니다. (제공되지 않으면 새 출력 배열이 생성됩니다.) 키워드 인수 `sorted`는 `v`가 정렬되어 있다고 가정할 수 있는지를 나타냅니다. `false`(기본값)인 경우, `v`의 요소는 제자리에서 부분적으로 정렬됩니다.

샘플 분위수는 `Q(p) = (1-γ)*x[j] + γ*x[j+1]`로 정의되며, 여기서 `x[j]`는 `v`의 j번째 순서 통계량이고, `j = floor(n*p + m)`, `m = alpha + p*(1 - alpha - beta)` 및 `γ = n*p + m - j`입니다.

기본적으로(`alpha = beta = 1`), 분위수는 점 `((k-1)/(n-1), x[k])` 사이의 선형 보간을 통해 계산됩니다. 여기서 `k = 1:n`이고 `n = length(v)`입니다. 이는 Hyndman과 Fan(1996)의 정의 7에 해당하며, R 및 NumPy의 기본값과 동일합니다.

키워드 인수 `alpha`와 `beta`는 Hyndman과 Fan의 동일한 매개변수에 해당하며, 이를 서로 다른 값으로 설정하면 이 논문에서 정의된 방법 4-9로 분위수를 계산할 수 있습니다:

  * Def. 4: `alpha=0`, `beta=1`
  * Def. 5: `alpha=0.5`, `beta=0.5` (MATLAB 기본값)
  * Def. 6: `alpha=0`, `beta=0` (Excel `PERCENTILE.EXC`, Python 기본값, Stata `altdef`)
  * Def. 7: `alpha=1`, `beta=1` (Julia, R 및 NumPy 기본값, Excel `PERCENTILE` 및 `PERCENTILE.INC`, Python `'inclusive'`)
  * Def. 8: `alpha=1/3`, `beta=1/3`
  * Def. 9: `alpha=3/8`, `beta=3/8`

!!! note
    `v`에 `NaN` 또는 [`missing`](@ref) 값이 포함된 경우 `ArgumentError`가 발생합니다.


# References

  * Hyndman, R.J and Fan, Y. (1996) "Sample Quantiles in Statistical Packages", *The American Statistician*, Vol. 50, No. 4, pp. 361-365
  * [Quantile on Wikipedia](https://en.m.wikipedia.org/wiki/Quantile)는 다양한 분위수 정의에 대한 세부 정보를 제공합니다.

# Examples

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
