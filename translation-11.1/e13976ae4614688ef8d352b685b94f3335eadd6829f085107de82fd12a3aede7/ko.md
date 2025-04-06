```
oneunit(x::T)
oneunit(T::Type)
```

`T(one(x))`를 반환합니다. 여기서 `T`는 인수의 유형이거나(유형이 전달된 경우) 인수입니다. 이는 차원 있는 양에 대한 [`one`](@ref)와 다릅니다: `one`은 차원이 없는(곱셈 항등원) 반면 `oneunit`은 차원 있는(x와 동일한 유형이거나 유형 `T`의) 것입니다.

# 예시

```jldoctest
julia> oneunit(3.7)
1.0

julia> import Dates; oneunit(Dates.Day)
1 day
```
