```
isfile(path) -> Bool
```

如果 `path` 是一个常规文件，则返回 `true`，否则返回 `false`。

# 示例

```jldoctest
julia> isfile(homedir())
false

julia> filename = "test_file.txt";

julia> write(filename, "Hello world!");

julia> isfile(filename)
true

julia> rm(filename);

julia> isfile(filename)
false
```

另请参见 [`isdir`](@ref) 和 [`ispath`](@ref)。
