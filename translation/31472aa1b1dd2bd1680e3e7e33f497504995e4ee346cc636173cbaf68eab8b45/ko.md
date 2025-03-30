```
x || y
```

단락 평가 불리언 OR.

참고: [`|`](@ref), [`xor`](@ref), [`&&`](@ref).

# 예제

```jldoctest
julia> pi < 3 || ℯ < 3
true

julia> false || true || println("둘 다 참이 아닙니다!")
true
```
