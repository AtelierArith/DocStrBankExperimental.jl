```
//(num, den)
```

두 정수 또는 유리수를 나누어 [`Rational`](@ref) 결과를 제공합니다. 더 일반적으로, `//`는 정수 또는 유리 구성 요소가 있는 다른 숫자 유형의 정확한 유리 나누기에 사용할 수 있으며, 예를 들어 정수 구성 요소가 있는 복소수와 같은 경우입니다.

부동 소수점 ([`AbstractFloat`](@ref)) 인수는 `//`에 의해 허용되지 않습니다 (값이 유리하더라도). 인수는 [`Integer`](@ref), `Rational` 또는 그 조합의 하위 유형이어야 합니다.

# 예제

```jldoctest
julia> 3 // 5
3//5

julia> (3 // 5) // (2 // 1)
3//10

julia> (1+2im) // (3+4im)
11//25 + 2//25*im

julia> 1.0 // 2
ERROR: MethodError: no method matching //(::Float64, ::Int64)
[...]
```
