```
peel(iter)
```

返回第一个元素和一个迭代器，用于遍历其余元素。

如果迭代器为空，则返回 `nothing`（类似于 `iterate`）。

!!! compat "Julia 1.7"
    先前版本在迭代器为空时会抛出 BoundsError。


另请参见: [`Iterators.drop`](@ref), [`Iterators.take`](@ref).

# 示例

```jldoctest
julia> (a, rest) = Iterators.peel("abc");

julia> a
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)

julia> collect(rest)
2-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (category Ll: Letter, lowercase)
 'c': ASCII/Unicode U+0063 (category Ll: Letter, lowercase)
```
