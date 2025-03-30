```
Threads.Atomic{T}
```

持有类型为 `T` 的对象的引用，确保它仅以原子方式访问，即以线程安全的方式。

只有某些“简单”类型可以原子地使用，即原始布尔、整数和浮点类型。这些类型包括 `Bool`、`Int8`...`Int128`、`UInt8`...`UInt128`，以及 `Float16`...`Float64`。

新的原子对象可以从非原子值创建；如果未指定，则原子对象初始化为零。

可以使用 `[]` 符号访问原子对象：

# 示例

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> x[] = 1
1

julia> x[]
1
```

原子操作使用 `atomic_` 前缀，例如 [`atomic_add!`](@ref)、[`atomic_xchg!`](@ref) 等。
