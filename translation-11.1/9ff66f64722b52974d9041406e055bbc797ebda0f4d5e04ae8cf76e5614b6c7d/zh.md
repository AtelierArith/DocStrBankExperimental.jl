Lockable(value, lock = ReentrantLock())

创建一个 `Lockable` 对象，该对象包装 `value` 并将其与提供的 `lock` 关联。此对象支持 [`@lock`](@ref)、[`lock`](@ref)、[`trylock`](@ref)、[`unlock`](@ref)。要访问值，必须在持有锁的情况下索引可锁对象。

!!! compat "Julia 1.11"
    至少需要 Julia 1.11。


## 示例

```jldoctest
julia> locked_list = Base.Lockable(Int[]);

julia> @lock(locked_list, push!(locked_list[], 1)) # 必须持有锁才能访问值
1-element Vector{Int64}:
 1

julia> lock(summary, locked_list)
"1-element Vector{Int64}"
```
