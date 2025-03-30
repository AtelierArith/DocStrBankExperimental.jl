```
argmax(f, domain)
```

값 `x`를 `domain`에서 반환하여 `f(x)`가 최대화됩니다. `f(x)`에 대해 여러 최대값이 있는 경우 첫 번째 값이 찾아집니다.

`domain`은 비어 있지 않은 반복 가능해야 합니다.

값은 `isless`로 비교됩니다.

!!! compat "Julia 1.7"
    이 메서드는 Julia 1.7 이상이 필요합니다.


자세한 내용은 [`argmin`](@ref), [`findmax`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> argmax(abs, -10:5)
-10

julia> argmax(cos, 0:π/2:2π)
0.0
```
