```
flipsign(x, y)
```

`y`가 음수일 경우 `x`의 부호를 뒤집은 값을 반환합니다. 예를 들어 `abs(x) = flipsign(x,x)`입니다.

# 예시

```jldoctest
julia> flipsign(5, 3)
5

julia> flipsign(5, -3)
-5
```
