```
mod(x::Integer, r::AbstractUnitRange)
```

`r` 범위에서 `y`를 찾아라. 여기서 $x ≡ y (mod n)$이고, `n = length(r)`이다. 즉, `y = mod(x - first(r), n) + first(r)`이다.

자세한 내용은 [`mod1`](@ref)를 참조하라.

# 예제

```jldoctest
julia> mod(0, Base.OneTo(3))  # mod1(0, 3)
3

julia> mod(3, 0:2)  # mod(3, 3)
0
```

!!! compat "Julia 1.3"
    이 메서드는 최소한 Julia 1.3이 필요하다.

