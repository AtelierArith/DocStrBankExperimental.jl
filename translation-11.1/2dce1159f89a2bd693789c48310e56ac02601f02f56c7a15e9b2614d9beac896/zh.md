```
isdirpath(path::AbstractString) -> Bool
```

确定路径是否指向一个目录（例如，是否以路径分隔符结尾）。

# 示例

```jldoctest
julia> isdirpath("/home")
false

julia> isdirpath("/home/")
true
```
