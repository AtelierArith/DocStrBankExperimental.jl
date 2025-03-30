```
Iterators.filter(flt, itr)
```

给定一个谓词函数 `flt` 和一个可迭代对象 `itr`，返回一个可迭代对象，该对象在迭代时产生满足 `flt(x)` 的 `itr` 的元素 `x`。原始迭代器的顺序得以保留。

此函数是 *惰性* 的；也就是说，它保证在 $Θ(1)$ 时间内返回并使用 $Θ(1)$ 的额外空间，并且 `flt` 不会在调用 `filter` 时被调用。对 `flt` 的调用将在迭代返回的可迭代对象时进行。这些调用不会被缓存，并且在重新迭代时会进行重复调用。

!!! warning
    对从 `filter` 返回的迭代器进行后续 *惰性* 转换，例如 `Iterators.reverse` 或 `cycle`，也会延迟对 `flt` 的调用，直到收集或迭代返回的可迭代对象。如果过滤谓词是非确定性的，或者其返回值依赖于对 `itr` 的元素的迭代顺序，则与惰性转换的组合可能会导致意外的行为。如果这不可取，请确保 `flt` 是一个纯函数，或者在进一步转换之前收集中间的 `filter` 迭代器。


请参见 [`Base.filter`](@ref) 以获取对数组的急切过滤实现。

# 示例

```jldoctest
julia> f = Iterators.filter(isodd, [1, 2, 3, 4, 5])
Base.Iterators.Filter{typeof(isodd), Vector{Int64}}(isodd, [1, 2, 3, 4, 5])

julia> foreach(println, f)
1
3
5

julia> [x for x in [1, 2, 3, 4, 5] if isodd(x)]  # 收集一个基于 Iterators.filter 的生成器
3-element Vector{Int64}:
 1
 3
 5
```
