```
WeakRef(x)
```

`w = WeakRef(x)` 构造一个对 Julia 值 `x` 的 [弱引用](https://en.wikipedia.org/wiki/Weak_reference)：尽管 `w` 包含对 `x` 的引用，但它并不阻止 `x` 被垃圾回收。`w.value` 要么是 `x`（如果 `x` 尚未被垃圾回收），要么是 `nothing`（如果 `x` 已被垃圾回收）。

```jldoctest
julia> x = "a string"
"a string"

julia> w = WeakRef(x)
WeakRef("a string")

julia> GC.gc()

julia> w           # 通过 `x` 维护一个引用
WeakRef("a string")

julia> x = nothing # 清除引用

julia> GC.gc()

julia> w
WeakRef(nothing)
```
