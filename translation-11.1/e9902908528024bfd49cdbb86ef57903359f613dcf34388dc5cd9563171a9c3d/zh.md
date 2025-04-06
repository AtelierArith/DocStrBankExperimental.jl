```
isabspath(path::AbstractString) -> Bool
```

确定路径是否为绝对路径（以根目录开始）。

# 示例

```jldoctest
julia> isabspath("/home")
true

julia> isabspath("home")
false
```
