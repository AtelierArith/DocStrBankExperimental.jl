```
allunique(itr) -> Bool
allunique(f, itr) -> Bool
```

如果 `itr` 中的所有值在与 [`isequal`](@ref) 比较时都是不同的，则返回 `true`。或者如果 `[f(x) for x in itr]` 中的所有值都是不同的，则返回第二种方法。

请注意，`allunique(f, itr)` 可能会调用 `f` 少于 `length(itr)` 次。调用的确切次数被视为实现细节。

当输入已排序时，`allunique` 可能会使用专门的实现。

另请参见：[`unique`](@ref)，[`issorted`](@ref)，[`allequal`](@ref)。

!!! compat "Julia 1.11"
    方法 `allunique(f, itr)` 至少需要 Julia 1.11。


# 示例

```jldoctest
julia> allunique([1, 2, 3])
true

julia> allunique([1, 2, 1, 2])
false

julia> allunique(Real[1, 1.0, 2])
false

julia> allunique([NaN, 2.0, NaN, 4.0])
false

julia> allunique(abs, [1, -1, 2])
false
```
