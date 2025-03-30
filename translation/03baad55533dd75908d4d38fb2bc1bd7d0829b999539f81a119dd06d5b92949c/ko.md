```
eps(::Type{T}) where T<:AbstractFloat
eps()
```

부동 소수점 유형 `T`의 *머신 엡실론*을 반환합니다(`T = Float64`가 기본값). 이는 `typeof(one(T))`로 표현할 수 있는 다음으로 큰 값과 1 사이의 간격으로 정의되며, `eps(one(T))`와 동일합니다. (`eps(T)`는 `T`의 *상대 오차*에 대한 경계이므로, [`one`](@ref)과 같은 "무차원" 양입니다.)

# 예제

```jldoctest
julia> eps()
2.220446049250313e-16

julia> eps(Float32)
1.1920929f-7

julia> 1.0 + eps()
1.0000000000000002

julia> 1.0 + eps()/2
1.0
```
