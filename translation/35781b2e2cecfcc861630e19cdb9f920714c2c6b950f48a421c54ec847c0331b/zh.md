```
only(x)
```

返回集合 `x` 的唯一元素，如果集合包含零个或多个元素，则抛出 [`ArgumentError`](@ref)。

另见 [`first`](@ref), [`last`](@ref)。

!!! compat "Julia 1.4"
    此方法至少需要 Julia 1.4。


# 示例

```jldoctest
julia> only(["a"])
"a"

julia> only("a")
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)

julia> only(())
ERROR: ArgumentError: Tuple contains 0 elements, must contain exactly 1 element
Stacktrace:
[...]

julia> only(('a', 'b'))
ERROR: ArgumentError: Tuple contains 2 elements, must contain exactly 1 element
Stacktrace:
[...]
```
