```
isreal(x) -> Bool
```

`x` 또는 `x`의 모든 요소가 무한대와 NaN을 포함하여 어떤 실수와 수치적으로 같은지 테스트합니다. `isreal(x)`는 `isequal(x, real(x))`가 true인 경우 true입니다.

# 예제

```jldoctest
julia> isreal(5.)
true

julia> isreal(1 - 3im)
false

julia> isreal(Inf + 0im)
true

julia> isreal([4.; complex(0,1)])
false
```
