```
Broadcast.broadcastable(x)
```

`x` 또는 `x`와 유사한 객체를 반환하여 [`axes`](@ref), 인덱싱을 지원하고 그 타입이 [`ndims`](@ref)를 지원하도록 합니다.

`x`가 반복(iteration)을 지원하는 경우, 반환된 값은 [`collect(x)`](@ref)와 동일한 `axes` 및 인덱싱 동작을 가져야 합니다.

`x`가 `AbstractArray`가 아니지만 `axes`, 인덱싱을 지원하고 그 타입이 `ndims`를 지원하는 경우, `broadcastable(::typeof(x))`는 단순히 자신을 반환하도록 구현될 수 있습니다. 또한, `x`가 자신의 [`BroadcastStyle`](@ref)를 정의하는 경우, 사용자 정의 스타일에 효과가 있으려면 `broadcastable` 메서드를 정의하여 자신을 반환해야 합니다.

# 예제

```jldoctest
julia> Broadcast.broadcastable([1,2,3]) # 배열은 이미 axes와 인덱싱을 지원하므로 `identity`와 같음
3-element Vector{Int64}:
 1
 2
 3

julia> Broadcast.broadcastable(Int) # 타입은 axes, 인덱싱 또는 반복을 지원하지 않지만 일반적으로 스칼라로 사용됨
Base.RefValue{Type{Int64}}(Int64)

julia> Broadcast.broadcastable("hello") # 문자열은 반복과 일치하는 관습을 깨고 스칼라처럼 작동함
Base.RefValue{String}("hello")
```
