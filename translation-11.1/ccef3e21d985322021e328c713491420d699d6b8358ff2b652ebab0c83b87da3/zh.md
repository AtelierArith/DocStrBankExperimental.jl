```
Threads.atomic_min!(x::Atomic{T}, val::T) where T
```

原子性地将 `x` 和 `val` 的最小值存储在 `x` 中

原子性地执行 `x[] = min(x[], val)`。返回**旧**值。

有关更多详细信息，请参见 LLVM 的 `atomicrmw min` 指令。

# 示例

```jldoctest
julia> x = Threads.Atomic{Int}(7)
Base.Threads.Atomic{Int64}(7)

julia> Threads.atomic_min!(x, 5)
7

julia> x[]
5
```
