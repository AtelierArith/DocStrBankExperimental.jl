```
signbit(x)
```

`x`의 부호 값이 음수이면 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다.

또한 [`sign`](@ref) 및 [`copysign`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> signbit(-4)
true

julia> signbit(5)
false

julia> signbit(5.5)
false

julia> signbit(-4.1)
true
```
