```
Threads.atomic_cas!(x::Atomic{T}, cmp::T, newval::T) where T
```

原子比较并设置 `x`

原子地将 `x` 中的值与 `cmp` 进行比较。如果相等，则将 `newval` 写入 `x`。否则，保持 `x` 不变。返回 `x` 中的旧值。通过将返回的值与 `cmp` 进行比较（通过 `===`），可以知道 `x` 是否被修改，并且现在是否持有新值 `newval`。

有关更多详细信息，请参见 LLVM 的 `cmpxchg` 指令。

此函数可用于实现事务语义。在事务之前，记录 `x` 中的值。在事务之后，仅在此期间 `x` 未被修改的情况下存储新值。

# 示例

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 4, 2);

julia> x
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 3, 2);

julia> x
Base.Threads.Atomic{Int64}(2)
```
