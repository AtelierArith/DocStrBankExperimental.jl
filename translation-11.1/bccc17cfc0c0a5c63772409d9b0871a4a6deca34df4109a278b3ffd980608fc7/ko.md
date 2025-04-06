```
Symbol(x...) -> Symbol
```

인수의 문자열 표현을 함께 연결하여 [`Symbol`](@ref)를 생성합니다.

# 예제

```jldoctest
julia> Symbol("my", "name")
:myname

julia> Symbol("day", 4)
:day4
```
