```
AtomicMemory{T} == GenericMemory{:atomic, T, Core.CPU}
```

固定大小的 [`DenseVector{T}`](@ref DenseVector)。对其任何元素的访问都是原子的（使用 `:monotonic` 排序）。设置任何元素必须使用 `@atomic` 宏并明确指定排序。

!!! warning
    每个元素在访问时都是独立的原子，不能以非原子的方式设置。目前 `@atomic` 宏和更高级的接口尚未完成，但未来实现的构建块是内部内置函数 `Core.memoryrefget`、`Core.memoryrefset!`、`Core.memoryref_isassigned`、`Core.memoryrefswap!`、`Core.memoryrefmodify!` 和 `Core.memoryrefreplace!`。


有关详细信息，请参见 [Atomic Operations](@ref man-atomic-operations)

!!! compat "Julia 1.11"
    此类型需要 Julia 1.11 或更高版本。

