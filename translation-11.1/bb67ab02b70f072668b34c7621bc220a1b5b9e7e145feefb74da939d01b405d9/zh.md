```
allequal(itr) -> Bool
allequal(f, itr) -> Bool
```

如果 `itr` 中的所有值在与 [`isequal`](@ref) 比较时相等，则返回 `true`。或者如果 `[f(x) for x in itr]` 中的所有值相等，则返回 `true`，适用于第二种方法。

请注意，`allequal(f, itr)` 可能会调用 `f` 少于 `length(itr)` 次。调用的确切次数被视为实现细节。

另请参见：[`unique`](@ref)，[`allunique`](@ref)。

!!! compat "Julia 1.8"
    `allequal` 函数需要至少 Julia 1.8。


!!! compat "Julia 1.11"
    方法 `allequal(f, itr)` 需要至少 Julia 1.11。


# 示例

```jldoctest
julia> allequal([])
true

julia> allequal([1])
true

julia> allequal([1, 1])
true

julia> allequal([1, 2])
false

julia> allequal(Dict(:a => 1, :b => 1))
false

julia> allequal(abs2, [1, -1])
true
```
