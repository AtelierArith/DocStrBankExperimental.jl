```
normalize!(a::AbstractArray, p::Real=2)
```

就地归一化数组 `a`，使其 `p`-范数等于1，即 `norm(a, p) == 1`。另见 [`normalize`](@ref) 和 [`norm`](@ref)。
