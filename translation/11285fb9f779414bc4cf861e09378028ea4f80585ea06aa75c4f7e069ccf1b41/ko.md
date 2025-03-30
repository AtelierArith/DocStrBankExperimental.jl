```
isone(x)
```

`x`가 `one(x)`와 같으면 `true`를 반환합니다. `x`가 배열인 경우, 이는 `x`가 항등 행렬인지 확인합니다.

# 예시

```jldoctest
julia> isone(1.0)
true

julia> isone([1 0; 0 2])
false

julia> isone([1 0; 0 true])
true
```
