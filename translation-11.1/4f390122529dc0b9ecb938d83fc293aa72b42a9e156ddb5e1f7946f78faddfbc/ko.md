```
div(x, y, r::RoundingMode=RoundToZero)
```

유클리드(정수) 나눗셈의 몫. `x / y`를 계산하고, 반올림 모드 `r`에 따라 정수로 반올림합니다. 다시 말해, 다음과 같은 양입니다.

```
round(x / y, r)
```

중간 반올림 없이.

!!! compat "Julia 1.4"
    `RoundingMode`를 사용하는 세 개의 인수 메서드는 Julia 1.4 이상이 필요합니다.


또한 이 함수의 특수 사례인 [`fld`](@ref) 및 [`cld`](@ref)를 참조하십시오.

!!! compat "Julia 1.9"
    `RoundFromZero`는 최소한 Julia 1.9가 필요합니다.


# 예제:

```jldoctest
julia> div(4, 3, RoundToZero) # div(4, 3)와 일치
1
julia> div(4, 3, RoundDown) # fld(4, 3)와 일치
1
julia> div(4, 3, RoundUp) # cld(4, 3)와 일치
2
julia> div(5, 2, RoundNearest)
2
julia> div(5, 2, RoundNearestTiesAway)
3
julia> div(-5, 2, RoundNearest)
-2
julia> div(-5, 2, RoundNearestTiesAway)
-3
julia> div(-5, 2, RoundNearestTiesUp)
-2
julia> div(4, 3, RoundFromZero)
2
julia> div(-4, 3, RoundFromZero)
-2
```
