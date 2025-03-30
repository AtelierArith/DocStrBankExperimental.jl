```
filter(f, itr::SkipMissing{<:AbstractArray})
```

주어진 `SkipMissing` 반복기로 감싸인 배열과 유사한 벡터를 반환하지만, 모든 결측값과 `f`가 `false`를 반환하는 요소는 제거됩니다.

!!! compat "Julia 1.2"
    이 메서드는 Julia 1.2 이상이 필요합니다.


# 예제

```jldoctest
julia> x = [1 2; missing 4]
2×2 Matrix{Union{Missing, Int64}}:
 1         2
  missing  4

julia> filter(isodd, skipmissing(x))
1-element Vector{Int64}:
 1
```
