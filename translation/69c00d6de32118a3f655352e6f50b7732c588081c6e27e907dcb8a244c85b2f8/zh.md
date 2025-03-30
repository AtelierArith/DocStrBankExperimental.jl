```
setcpuaffinity(original_command::Cmd, cpus) -> command::Cmd
```

通过一组 CPU ID（基于 1 的索引）`cpus` 设置 `command` 的 CPU 亲和性。传递 `cpus = nothing` 意味着如果 `original_command` 有任何 CPU 亲和性，则取消设置。

此功能仅在 Linux 和 Windows 中受支持。在 macOS 中不受支持，因为 libuv 不支持亲和性设置。

!!! compat "Julia 1.8"
    此功能至少需要 Julia 1.8。


# 示例

在 Linux 中，可以使用 `taskset` 命令行程序查看 `setcpuaffinity` 的工作原理。

```julia
julia> run(setcpuaffinity(`sh -c 'taskset -p $$'`, [1, 2, 5]));
pid 2273's current affinity mask: 13
```

请注意，掩码值 `13` 反映出第一个、第二个和第五个位（从最低有效位开始计数）被打开：

```julia
julia> 0b010011
0x13
```
