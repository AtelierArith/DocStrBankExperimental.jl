```
norm(x::Number, p::Real=2)
```

숫자의 경우, $\left( |x|^p \right)^{1/p}$를 반환합니다.

# 예제

```jldoctest
julia> norm(2, 1)
2.0

julia> norm(-2, 1)
2.0

julia> norm(2, 2)
2.0

julia> norm(-2, 2)
2.0

julia> norm(2, Inf)
2.0

julia> norm(-2, Inf)
2.0
```
