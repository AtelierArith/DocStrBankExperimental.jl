```
<=(x, y)
≤(x,y)
```

작거나 같음 비교 연산자. `(x < y) | (x == y)`로 대체됩니다.

# 예제

```jldoctest
julia> 'a' <= 'b'
true

julia> 7 ≤ 7 ≤ 9
true

julia> "abc" ≤ "abc"
true

julia> 5 <= 3
false
```
