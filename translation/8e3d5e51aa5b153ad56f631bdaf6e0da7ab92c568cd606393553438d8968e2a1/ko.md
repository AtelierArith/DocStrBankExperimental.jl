```
popat!(a::Vector, i::Integer, [default])
```

주어진 `i`에서 항목을 제거하고 반환합니다. 이후 항목들은 결과적으로 생긴 간격을 채우기 위해 이동됩니다. `i`가 `a`에 대한 유효한 인덱스가 아닐 경우, `default`를 반환하거나 `default`가 지정되지 않은 경우 오류를 발생시킵니다.

참고: [`pop!`](@ref), [`popfirst!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref).

!!! compat "Julia 1.5"
    이 함수는 Julia 1.5부터 사용할 수 있습니다.


# 예제

```jldoctest
julia> a = [4, 3, 2, 1]; popat!(a, 2)
3

julia> a
3-element Vector{Int64}:
 4
 2
 1

julia> popat!(a, 4, missing)
missing

julia> popat!(a, 4)
ERROR: BoundsError: attempt to access 3-element Vector{Int64} at index [4]
[...]
```
