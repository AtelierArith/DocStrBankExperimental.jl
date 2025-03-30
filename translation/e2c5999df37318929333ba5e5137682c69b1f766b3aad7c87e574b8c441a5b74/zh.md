```
isreadable(path::String)
```

如果给定 `path` 的访问权限允许当前用户读取，则返回 `true`。

!!! note
    在用户调用 `open` 之前，这个权限可能会改变，因此建议仅调用 `open` 并在失败时处理错误，而不是先调用 `isreadable`。


!!! note
    目前此函数无法正确查询 Windows 上的文件系统 ACL，因此可能返回错误结果。


!!! compat "Julia 1.11"
    此函数至少需要 Julia 1.11。


另请参见 [`ispath`](@ref), [`isexecutable`](@ref), [`iswritable`](@ref)。
