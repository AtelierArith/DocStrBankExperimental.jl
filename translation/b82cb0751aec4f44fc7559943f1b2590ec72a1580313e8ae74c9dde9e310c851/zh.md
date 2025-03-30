```
broadcast!(f, dest, As...)
```

像 [`broadcast`](@ref) 一样，但将 `broadcast(f, As...)` 的结果存储在 `dest` 数组中。请注意，`dest` 仅用于存储结果，并不提供 `f` 的参数，除非它也在 `As` 中列出，例如 `broadcast!(f, A, A, B)` 来执行 `A[:] = broadcast(f, A, B)`。

# 示例

```jldoctest
julia> A = [1.0; 0.0]; B = [0.0; 0.0];

julia> broadcast!(+, B, A, (0, -2.0));

julia> B
2-element Vector{Float64}:
  1.0
 -2.0

julia> A
2-element Vector{Float64}:
 1.0
 0.0

julia> broadcast!(+, A, A, (0, -2.0));

julia> A
2-element Vector{Float64}:
  1.0
 -2.0
```
