```
Threads.atomic_sub!(x::Atomic{T}, val::T) where T <: ArithmeticTypes
```

原子地从 `x` 中减去 `val`

原子地执行 `x[] -= val`。返回**旧**值。未定义于 `Atomic{Bool}`。

有关更多详细信息，请参见 LLVM 的 `atomicrmw sub` 指令。

# 示例

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_sub!(x, 2)
3

julia> x[]
1
```
