```
splitext(path::AbstractString) -> (String, String)
```

如果路径的最后一个组件包含一个或多个点，则将路径拆分为最后一个点之前的所有内容和包括点及其后面的所有内容。否则，返回未修改的参数元组和空字符串。“splitext”是“split extension”的缩写。

# 示例

```jldoctest
julia> splitext("/home/myuser/example.jl")
("/home/myuser/example", ".jl")

julia> splitext("/home/myuser/example.tar.gz")
("/home/myuser/example.tar", ".gz")

julia> splitext("/home/my.user/example")
("/home/my.user/example", "")
```
