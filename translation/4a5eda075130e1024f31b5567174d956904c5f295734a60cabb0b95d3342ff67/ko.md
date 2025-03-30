```
>=(x, y)
≥(x,y)
```

크거나 같은 비교 연산자. `y <= x`로 대체됩니다.

# 예제

```jldoctest
julia> 'a' >= 'b'
false

julia> 7 ≥ 7 ≥ 3
true

julia> "abc" ≥ "abc"
true

julia> 5 >= 3
true
```
