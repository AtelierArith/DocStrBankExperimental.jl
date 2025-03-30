```
homedir() -> String
```

返回当前用户的主目录。

!!! note
    `homedir` 通过 `libuv` 的 `uv_os_homedir` 确定主目录。有关详细信息（例如如何通过环境变量指定主目录），请参见 [`uv_os_homedir` 文档](http://docs.libuv.org/en/v1.x/misc.html#c.uv_os_homedir)。


另见 [`Sys.username`](@ref).
