```
GC.@preserve x1 x2 ... xn expr
```

在评估表达式 `expr` 的过程中，将对象 `x1, x2, ...` 标记为 *正在使用中*。这仅在不安全代码中需要，其中 `expr` *隐式使用* 由 `x` 中的一个拥有的内存或其他资源。

`x` 的 *隐式使用* 涉及任何逻辑上由 `x` 拥有的资源的间接使用，编译器无法看到。一些示例：

  * 通过 `Ptr` 直接访问对象的内存
  * 将指针传递给 `x` 到 `ccall`
  * 使用 `x` 的资源，这些资源将在终结器中被清理。

`@preserve` 通常在典型用例中不会对性能产生任何影响，因为它只是短暂地延长了对象的生命周期。在实现中，`@preserve` 具有保护动态分配对象免受垃圾回收的效果。

# 示例

当使用 `unsafe_load` 从指针加载时，底层对象被隐式使用，例如 `unsafe_load(p)` 中隐式使用了 `x`，如下所示：

```jldoctest
julia> let
           x = Ref{Int}(101)
           p = Base.unsafe_convert(Ptr{Int}, x)
           GC.@preserve x unsafe_load(p)
       end
101
```

在将指针传递给 `ccall` 时，被指向的对象被隐式使用并应被保留。（但请注意，通常应直接将 `x` 传递给 `ccall`，这算作显式使用。）

```jldoctest
julia> let
           x = "Hello"
           p = pointer(x)
           Int(GC.@preserve x @ccall strlen(p::Cstring)::Csize_t)
           # 优选替代方案
           Int(@ccall strlen(x::Cstring)::Csize_t)
       end
5
```
