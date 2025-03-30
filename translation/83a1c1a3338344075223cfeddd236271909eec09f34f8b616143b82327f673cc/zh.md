```
Threads.atomic_and!(x::Atomic{T}, val::T) where T
```

原子性地对 `x` 和 `val` 进行按位与操作

原子性地执行 `x[] &= val`。返回**旧**值。

有关更多详细信息，请参见 LLVM 的 `atomicrmw and` 指令。

# 示例

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_and!(x, 2)
3

julia> x[]
2
```
