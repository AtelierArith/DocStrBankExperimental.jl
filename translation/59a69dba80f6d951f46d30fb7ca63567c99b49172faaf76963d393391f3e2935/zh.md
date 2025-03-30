```
empty(v::AbstractVector, [eltype])
```

创建一个与 `v` 类似的空向量，选项上可以更改 `eltype`。

另见: [`empty!`](@ref), [`isempty`](@ref), [`isassigned`](@ref)。

# 示例

```jldoctest
julia> empty([1.0, 2.0, 3.0])
Float64[]

julia> empty([1.0, 2.0, 3.0], String)
String[]
```
