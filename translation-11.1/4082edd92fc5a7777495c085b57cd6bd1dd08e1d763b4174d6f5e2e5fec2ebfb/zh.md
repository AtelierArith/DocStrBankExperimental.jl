```
isexecutable(path::String)
```

如果给定的 `path` 具有可执行权限，则返回 `true`。

!!! note
    在用户执行 `path` 之前，这个权限可能会改变，因此建议执行文件并处理错误（如果失败），而不是先调用 `isexecutable`。


!!! note
    在 Julia 1.6 之前，这个函数无法正确查询 Windows 上的文件系统 ACL，因此它会对任何文件返回 `true`。从 Julia 1.6 开始，它能够正确判断文件是否被标记为可执行。


另请参见 [`ispath`](@ref)，[`isreadable`](@ref)，[`iswritable`](@ref)。
