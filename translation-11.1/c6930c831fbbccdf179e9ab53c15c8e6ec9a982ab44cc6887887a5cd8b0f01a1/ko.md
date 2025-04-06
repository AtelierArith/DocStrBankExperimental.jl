```
nextprod(factors::Union{Tuple,AbstractVector}, n)
```

`n` 이상인 다음 정수로, `factors`에 있는 인수 $k_i$에 대해 정수 $p_1$, $p_2$ 등을 사용하여 $\prod k_i^{p_i}$로 표현될 수 있습니다.

# 예시

```jldoctest
julia> nextprod((2, 3), 105)
108

julia> 2^2 * 3^3
108
```

!!! compat "Julia 1.6"
    튜플을 허용하는 메서드는 Julia 1.6 이상이 필요합니다.

