```
Val(c)
```

`Val{c}()`를 반환합니다. 이 객체는 런타임 데이터가 포함되어 있지 않습니다. 이러한 유형은 `c` 값을 통해 함수 간에 정보를 전달하는 데 사용할 수 있으며, `c`는 `isbits` 값 또는 `Symbol`이어야 합니다. 이 구조의 의도는 런타임에 상수의 값을 테스트하지 않고도 상수에 직접적으로 분기할 수 있도록 하는 것입니다.

# 예제

```jldoctest
julia> f(::Val{true}) = "Good"
f (generic function with 1 method)

julia> f(::Val{false}) = "Bad"
f (generic function with 2 methods)

julia> f(Val(true))
"Good"
```
