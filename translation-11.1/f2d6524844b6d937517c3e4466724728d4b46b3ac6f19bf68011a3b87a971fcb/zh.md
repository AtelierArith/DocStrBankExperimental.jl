```
Threads.atomic_or!(x::Atomic{T}, val::T) where T
```

原子性地对 `x` 和 `val` 进行按位或操作

原子性地执行 `x[] |= val`。返回**旧**值。

有关更多详细信息，请参见 LLVM 的 `atomicrmw or` 指令。

# 示例

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_or!(x, 7)
5

julia> x[]
7
```
