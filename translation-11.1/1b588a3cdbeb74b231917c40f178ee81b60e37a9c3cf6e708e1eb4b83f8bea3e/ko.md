```
함수
```

모든 함수의 추상 유형입니다.

# 예제

```jldoctest
julia> isa(+, Function)
true

julia> typeof(sin)
typeof(sin) (함수 sin의 단일 유형, Function의 하위 유형)

julia> ans <: Function
true
```
