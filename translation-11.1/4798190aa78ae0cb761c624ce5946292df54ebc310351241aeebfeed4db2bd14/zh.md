```
ENV
```

对单例 `EnvDict` 的引用，提供了一个字典接口来访问系统环境变量。

（在 Windows 上，系统环境变量不区分大小写，因此 `ENV` 相应地将所有键转换为大写以便于显示、迭代和复制。可移植的代码不应依赖于通过大小写区分变量的能力，并应注意设置一个表面上是小写的变量可能会导致大写的 `ENV` 键。）

!!! warning
    修改环境不是线程安全的。


# 示例

```julia-repl
julia> ENV
Base.EnvDict with "50" entries:
  "SECURITYSESSIONID"            => "123"
  "USER"                         => "username"
  "MallocNanoZone"               => "0"
  ⋮                              => ⋮

julia> ENV["JULIA_EDITOR"] = "vim"
"vim"

julia> ENV["JULIA_EDITOR"]
"vim"
```

另见: [`withenv`](@ref), [`addenv`](@ref).
