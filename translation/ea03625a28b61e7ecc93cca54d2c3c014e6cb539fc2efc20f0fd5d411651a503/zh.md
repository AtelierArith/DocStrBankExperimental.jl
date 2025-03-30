```
addprocs(machines; tunnel=false, sshflags=``, max_parallel=10, kwargs...) -> 进程标识符列表
```

通过 SSH 在远程机器上添加工作进程。配置通过关键字参数完成（见下文）。特别是，`exename` 关键字可用于指定远程机器上的 `julia` 二进制文件的路径。

`machines` 是一个“机器规格”的向量，格式为 `[user@]host[:port] [bind_addr[:port]]` 的字符串。`user` 默认为当前用户，`port` 默认为标准 SSH 端口。如果指定了 `[bind_addr[:port]]`，其他工作进程将通过指定的 `bind_addr` 和 `port` 连接到此工作进程。

可以通过在 `machines` 向量中使用元组或形式 `(machine_spec, count)` 来在远程主机上启动多个进程，其中 `count` 是要在指定主机上启动的工作进程数量。将 `:auto` 作为工作进程数量传递将启动与远程主机上的 CPU 线程数量相同的工作进程。

**示例**：

```julia
addprocs([
    "remote1",               # 在 'remote1' 上以当前用户名登录的一个工作进程
    "user@remote2",          # 在 'remote2' 上以 'user' 用户名登录的一个工作进程
    "user@remote3:2222",     # 为 'remote3' 指定 SSH 端口为 '2222'
    ("user@remote4", 4),     # 在 'remote4' 上启动 4 个工作进程
    ("user@remote5", :auto), # 在 'remote5' 上启动与 CPU 线程数量相同的工作进程
])
```

**关键字参数**：

  * `tunnel`：如果为 `true`，则将使用 SSH 隧道从主进程连接到工作进程。默认值为 `false`。
  * `multiplex`：如果为 `true`，则在 SSH 隧道中使用 SSH 复用。默认值为 `false`。
  * `ssh`：用于启动工作进程的 SSH 客户端可执行文件的名称或路径。默认值为 `"ssh"`。
  * `sshflags`：指定额外的 ssh 选项，例如 ```sshflags=`-i /home/foo/bar.pem` ```
  * `max_parallel`：指定在主机上并行连接的最大工作进程数量。默认值为 10。
  * `shell`：指定 SSH 在工作进程上连接的 shell 类型。

      * `shell=:posix`：兼容 POSIX 的 Unix/Linux shell（sh、ksh、bash、dash、zsh 等）。默认值。
      * `shell=:csh`：Unix C shell（csh、tcsh）。
      * `shell=:wincmd`：Microsoft Windows `cmd.exe`。
  * `dir`：指定工作进程上的工作目录。默认值为主机的当前目录（通过 `pwd()` 找到）。
  * `enable_threaded_blas`：如果为 `true`，则 BLAS 将在添加的进程中以多个线程运行。默认值为 `false`。
  * `exename`：`julia` 可执行文件的名称。默认值为 `"$(Sys.BINDIR)/julia"` 或 `"$(Sys.BINDIR)/julia-debug"`，具体取决于情况。建议在所有远程机器上使用相同的 Julia 版本，因为否则序列化和代码分发可能会失败。
  * `exeflags`：传递给工作进程的额外标志。
  * `topology`：指定工作进程之间的连接方式。在未连接的工作进程之间发送消息会导致错误。

      * `topology=:all_to_all`：所有进程彼此连接。默认值。
      * `topology=:master_worker`：只有驱动进程，即 `pid` 1 连接到工作进程。工作进程之间不相互连接。
      * `topology=:custom`：集群管理器的 `launch` 方法通过 `WorkerConfig` 中的 `ident` 和 `connect_idents` 字段指定连接拓扑。具有集群管理器身份 `ident` 的工作进程将连接到 `connect_idents` 中指定的所有工作进程。
  * `lazy`：仅适用于 `topology=:all_to_all`。如果为 `true`，则工作进程之间的连接是懒惰设置的，即在工作进程之间的第一次远程调用时设置。默认值为 true。
  * `env`：提供一个字符串对数组，例如 `env=["JULIA_DEPOT_PATH"=>"/depot"]`，以请求在远程机器上设置环境变量。默认情况下，只有环境变量 `JULIA_WORKER_TIMEOUT` 会自动从本地传递到远程环境。
  * `cmdline_cookie`：通过 `--worker` 命令行选项传递身份验证 cookie。通过 ssh stdio 传递 cookie 的（更安全的）默认行为可能会在使用较旧（预 ConPTY）Julia 或 Windows 版本的 Windows 工作进程中挂起，在这种情况下，`cmdline_cookie=true` 提供了一种解决方法。

!!! compat "Julia 1.6"
    关键字参数 `ssh`、`shell`、`env` 和 `cmdline_cookie` 在 Julia 1.6 中添加。


环境变量：

如果主进程在 60.0 秒内未能与新启动的工作进程建立连接，则该工作进程将其视为致命情况并终止。此超时可以通过环境变量 `JULIA_WORKER_TIMEOUT` 控制。主进程上的 `JULIA_WORKER_TIMEOUT` 的值指定新启动的工作进程等待建立连接的秒数。
