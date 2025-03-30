```
cmp(x,y)
```

`x`가 `y`보다 작으면 -1, 같으면 0, 크면 1을 반환합니다. `isless`에 의해 구현된 전체 순서를 사용합니다.

# 예제

```jldoctest
julia> cmp(1, 2)
-1

julia> cmp(2, 1)
1

julia> cmp(2+im, 3-im)
ERROR: MethodError: no method matching isless(::Complex{Int64}, ::Complex{Int64})
[...]
```
