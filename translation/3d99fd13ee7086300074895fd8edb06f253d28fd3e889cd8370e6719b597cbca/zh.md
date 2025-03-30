```
splitdir(path::AbstractString) -> (AbstractString, AbstractString)
```

将路径拆分为目录名和文件名的元组。

# 示例

```jldoctest
julia> splitdir("/home/myuser")
("/home", "myuser")
```
