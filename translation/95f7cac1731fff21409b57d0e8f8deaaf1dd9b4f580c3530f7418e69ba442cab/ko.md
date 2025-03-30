```
copysign(x, y) -> z
```

`x`의 크기를 가지며 `y`와 같은 부호를 가진 `z`를 반환합니다.

# 예제

```jldoctest
julia> copysign(1, -2)
-1

julia> copysign(-1, 2)
1
```
