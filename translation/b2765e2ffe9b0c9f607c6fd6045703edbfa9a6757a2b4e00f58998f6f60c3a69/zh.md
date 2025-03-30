```
Threads.atomic_xchg!(x::Atomic{T}, newval::T) where T
```

原子性地交换 `x` 中的值

原子性地将 `x` 中的值与 `newval` 交换。返回**旧**值。

有关更多详细信息，请参见 LLVM 的 `atomicrmw xchg` 指令。

# 示例

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_xchg!(x, 2)
3

julia> x[]
2
```
