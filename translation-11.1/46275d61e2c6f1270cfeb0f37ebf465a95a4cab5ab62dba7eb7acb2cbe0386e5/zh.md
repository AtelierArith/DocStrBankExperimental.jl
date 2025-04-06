```
mktemp(f::Function, parent=tempdir())
```

将函数 `f` 应用到 [`mktemp(parent)`](@ref) 的结果，并在完成后删除临时文件。

另见: [`mktempdir`](@ref).
