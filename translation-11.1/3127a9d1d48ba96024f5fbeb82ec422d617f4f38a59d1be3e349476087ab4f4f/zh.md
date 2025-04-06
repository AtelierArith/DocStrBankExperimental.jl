```
Threads.atomic_add!(x::Atomic{T}, val::T) where T <: ArithmeticTypes
```

原子地将 `val` 加到 `x` 上

以原子方式执行 `x[] += val`。返回 **旧** 值。未定义于 `Atomic{Bool}`。

有关更多详细信息，请参见 LLVM 的 `atomicrmw add` 指令。

# 示例

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_add!(x, 2)
3

julia> x[]
5
```
