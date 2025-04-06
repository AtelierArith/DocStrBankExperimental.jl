```
findlast(ch::AbstractChar, string::AbstractString)
```

查找字符 `ch` 在 `string` 中的最后一次出现。

!!! compat "Julia 1.3"
    此方法至少需要 Julia 1.3。


# 示例

```jldoctest
julia> findlast('p', "happy")
4

julia> findlast('z', "happy") === nothing
true
```
