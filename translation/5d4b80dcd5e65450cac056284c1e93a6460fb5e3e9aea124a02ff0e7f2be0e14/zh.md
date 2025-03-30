```
Threads.atomic_max!(x::Atomic{T}, val::T) where T
```

原子性地将 `x` 和 `val` 的最大值存储在 `x` 中

原子性地执行 `x[] = max(x[], val)`。返回**旧**值。

有关更多详细信息，请参见 LLVM 的 `atomicrmw max` 指令。

# 示例

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_max!(x, 7)
5

julia> x[]
7
```
