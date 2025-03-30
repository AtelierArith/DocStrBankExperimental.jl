```
Sys.username() -> String
```

返回当前用户的用户名。如果无法确定用户名或用户名为空，则此函数会抛出错误。

要检索可以通过环境变量覆盖的用户名，例如 `USER`，可以考虑使用

```julia
user = get(Sys.username, ENV, "USER")
```

!!! compat "Julia 1.11"
    此函数至少需要 Julia 1.11。


另请参见 [`homedir`](@ref).
