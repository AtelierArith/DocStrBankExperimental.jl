```
divrem(x, y, r::RoundingMode=RoundToZero)
```

유클리드 나눗셈에서의 몫과 나머지. `(div(x, y, r), rem(x, y, r))`와 동등합니다. 기본값 `r`을 사용하면 이 호출은 `(x ÷ y, x % y)`와 동등합니다.

참고: [`fldmod`](@ref), [`cld`](@ref).

# 예제

```jldoctest
julia> divrem(3, 7)
(0, 3)

julia> divrem(7, 3)
(2, 1)
```
