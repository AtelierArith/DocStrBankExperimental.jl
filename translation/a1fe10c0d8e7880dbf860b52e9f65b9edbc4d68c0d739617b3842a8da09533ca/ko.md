```
eigvals(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> values
```

`A`의 고유값을 반환합니다. 정렬된 고유값의 인덱스를 포함하는 [`UnitRange`](@ref) `irange`를 지정하여 고유값의 하위 집합만 계산할 수 있습니다. 예를 들어, 2번째에서 8번째 고유값을 계산할 수 있습니다.

# 예제

```jldoctest
julia> A = SymTridiagonal([1.; 2.; 1.], [2.; 3.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 1.0  2.0   ⋅
 2.0  2.0  3.0
  ⋅   3.0  1.0

julia> eigvals(A, 2:2)
1-element Vector{Float64}:
 0.9999999999999996

julia> eigvals(A)
3-element Vector{Float64}:
 -2.1400549446402604
  1.0000000000000002
  5.140054944640259
```
