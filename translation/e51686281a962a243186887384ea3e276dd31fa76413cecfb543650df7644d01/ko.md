```
isa(x, type) -> Bool
```

주어진 `type`의 `x`가 있는지 확인합니다. 또한 중위 연산자로 사용할 수 있습니다. 예: `x isa type`.

# 예제

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, Matrix)
false

julia> isa(1, Char)
false

julia> isa(1, Number)
true

julia> 1 isa Number
true
```
