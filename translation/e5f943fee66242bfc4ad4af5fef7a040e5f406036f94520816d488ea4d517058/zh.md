```
abspath(path::AbstractString) -> String
```

通过在必要时添加当前目录，将路径转换为绝对路径。还会像 [`normpath`](@ref) 一样规范化路径。

# 示例

如果您在一个名为 `JuliaExample` 的目录中，并且您使用的数据相对于 `JuliaExample` 目录在上面两级，您可以写：

```
abspath("../../data")
```

这将给出类似 `"/home/JuliaUser/data/"` 的路径。

另请参见 [`joinpath`](@ref)，[`pwd`](@ref)，[`expanduser`](@ref)。
