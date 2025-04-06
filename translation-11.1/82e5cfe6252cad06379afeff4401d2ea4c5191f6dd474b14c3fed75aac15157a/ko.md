```
keepat!(a::Vector, m::AbstractVector{Bool})
keepat!(a::BitVector, m::AbstractVector{Bool})
```

논리 인덱싱의 제자리 버전 `a = a[m]`. 즉, 길이가 같은 벡터 `a`와 `m`에 대해 `keepat!(a, m)`을 사용하면, 해당 인덱스에서 `m`이 `false`인 `a`의 모든 요소가 제거됩니다.

# 예제

```jldoctest
julia> a = [:a, :b, :c];

julia> keepat!(a, [true, false, true])
2-element Vector{Symbol}:
 :a
 :c

julia> a
2-element Vector{Symbol}:
 :a
 :c
```
