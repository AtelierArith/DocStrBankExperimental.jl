```
argmin(f, domain)
```

`f(x)`가 최소화되는 `domain`에서 값을 `x`로 반환합니다. `f(x)`에 대해 여러 개의 최소값이 있는 경우 첫 번째 값이 찾아집니다.

`domain`은 비어 있지 않은 반복 가능해야 합니다.

`NaN`은 `missing`을 제외한 모든 다른 값보다 작게 처리됩니다.

!!! compat "Julia 1.7"
    이 메서드는 Julia 1.7 이상이 필요합니다.


자세한 내용은 [`argmax`](@ref), [`findmin`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> argmin(sign, -10:5)
-10

julia> argmin(x -> -x^3 + x^2 - 10, -5:5)
5

julia> argmin(acos, 0:0.1:1)
1.0
```
