```
addprocs(np::Integer=Sys.CPU_THREADS; restrict=true, kwargs...) -> 进程标识符列表
```

使用内置的 `LocalManager` 在本地主机上启动 `np` 个工作进程。

本地工作进程从主进程继承当前的包环境（即活动项目、[`LOAD_PATH`](@ref) 和 [`DEPOT_PATH`](@ref)）。

!!! warning
    请注意，工作进程不会运行 `~/.julia/config/startup.jl` 启动脚本，也不会与其他正在运行的进程同步其全局状态（例如命令行开关、全局变量、新方法定义和加载的模块）。


**关键字参数**：

  * `restrict::Bool`：如果为 `true`（默认），绑定限制为 `127.0.0.1`。
  * `dir`、`exename`、`exeflags`、`env`、`topology`、`lazy`、`enable_threaded_blas`：与 `SSHManager` 的效果相同，参见 [`addprocs(machines::AbstractVector)`](@ref) 的文档。

!!! compat "Julia 1.9"
    包环境的继承和 `env` 关键字参数是在 Julia 1.9 中添加的。

