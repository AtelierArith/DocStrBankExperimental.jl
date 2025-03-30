```
Base.isambiguous(m1, m2; ambiguous_bottom=false) -> Bool
```

确定两个方法 `m1` 和 `m2` 是否可能在某些调用签名中产生歧义。此测试是在同一函数的其他方法的上下文中进行的；在孤立情况下，`m1` 和 `m2` 可能是模糊的，但如果定义了一个解决歧义的第三个方法，则返回 `false`。或者，在孤立情况下，`m1` 和 `m2` 可能是有序的，但如果无法与它们排序的第三个方法存在，它们可能会一起导致歧义。

对于参数化类型，`ambiguous_bottom` 关键字参数控制 `Union{}` 是否被视为类型参数的模糊交集——当 `true` 时，它被视为模糊，当 `false` 时则不是。

# 示例

```jldoctest
julia> foo(x::Complex{<:Integer}) = 1
foo (generic function with 1 method)

julia> foo(x::Complex{<:Rational}) = 2
foo (generic function with 2 methods)

julia> m1, m2 = collect(methods(foo));

julia> typeintersect(m1.sig, m2.sig)
Tuple{typeof(foo), Complex{Union{}}}

julia> Base.isambiguous(m1, m2, ambiguous_bottom=true)
true

julia> Base.isambiguous(m1, m2, ambiguous_bottom=false)
false
```
