```
chmod(path::AbstractString, mode::Integer; recursive::Bool=false)
```

将 `path` 的权限模式更改为 `mode`。目前仅支持整数 `mode`（例如 `0o777`）。如果 `recursive=true` 且路径是一个目录，则该目录中的所有权限将被递归更改。返回 `path`。

!!! note
    在 Julia 1.6 之前，这在 Windows 上无法正确操作文件系统 ACL，因此它只会在文件上设置只读位。现在它能够操作 ACL。

