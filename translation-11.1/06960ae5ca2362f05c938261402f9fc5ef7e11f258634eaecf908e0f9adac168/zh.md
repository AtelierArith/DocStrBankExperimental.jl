```
setenv(command::Cmd, env; dir)
```

设置在运行给定 `command` 时使用的环境变量。`env` 可以是一个将字符串映射到字符串的字典，一个形式为 `"var=val"` 的字符串数组，或者零个或多个 `"var"=>val` 对参数。为了修改（而不是替换）现有环境，可以通过 `copy(ENV)` 创建 `env`，然后根据需要设置 `env["var"]=val`，或者使用 [`addenv`](@ref)。

`dir` 关键字参数可用于指定命令的工作目录。`dir` 默认为 `command` 当前设置的 `dir`（如果未指定，则为当前工作目录）。

另请参见 [`Cmd`](@ref)，[`addenv`](@ref)，[`ENV`](@ref)，[`pwd`](@ref)。
