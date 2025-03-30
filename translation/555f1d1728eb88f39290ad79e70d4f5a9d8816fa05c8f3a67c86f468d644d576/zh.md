# External Profiler Support

Julia 提供对一些外部跟踪分析器的明确支持，使您能够获得运行时执行行为的高层次概述。

当前支持的分析器有：

  * [Tracy](https://github.com/wolfpld/tracy)
  * [Intel VTune (ITTAPI)](https://github.com/intel/ittapi)

### Adding New Zones

要添加新区域，请使用 `JL_TIMING` 宏。您可以通过搜索 `JL_TIMING` 在代码库中找到许多示例。要添加一种新类型的区域，您需要将其添加到 `JL_TIMING_OWNERS`（可能还包括 `JL_TIMING_EVENTS`）。

### Dynamically Enabling and Disabling Zones

[`JULIA_TIMING_SUBSYSTEMS`](@ref JULIA_TIMING_SUBSYSTEMS) 环境变量允许您为特定的 Julia 运行启用或禁用区域。例如，将变量设置为 `+GC,-INFERENCE` 将启用 `GC` 区域并禁用 `INFERENCE` 区域。

## Tracy Profiler

[Tracy](https://github.com/wolfpld/tracy) 是一个灵活的分析器，可以选择性地与 Julia 集成。

一个典型的Tracy会话可能看起来像这样：

![典型的Tracy使用](tracy.png)

### Building Julia with Tracy

要启用Tracy集成，请在`Make.user`文件中使用额外选项`WITH_TRACY=1`构建Julia。

### Installing the Tracy Profile Viewer

获取配置文件查看器的最简单方法是添加 `TracyProfiler_jll` 包并通过以下命令启动分析器：

```julia
run(TracyProfiler_jll.tracy())
```

!!! note
    在 macOS 上，如果分析器中的 UI 元素显得过大，您可能想将 `TRACY_DPI_SCALE` 环境变量设置为 `1.0`。


要运行一个“无头”实例并将跟踪保存到磁盘，请使用

```julia
run(`$(TracyProfiler_jll.capture()) -o mytracefile.tracy`)
```

相反。

有关使用Tracy UI的信息，请参阅Tracy手册。

### Profiling Julia with Tracy

使用Tracy对Julia进行性能分析的典型工作流程包括通过以下方式启动Julia：

```julia
JULIA_WAIT_FOR_TRACY=1 ./julia -e '...'
```

环境变量确保 Julia 在成功连接到 Tracy 分析器之前等待，才能继续执行。之后，使用 Tracy 分析器 UI，点击 `Connect`，Julia 执行应该恢复，分析应该开始。

### Profiling package precompilation with Tracy

要对包的预编译过程进行分析，最简单的方法是显式调用 `Base.compilecache`，并传入您想要预编译的包：

```julia
pkg = Base.identify_package("SparseArrays")
withenv("JULIA_WAIT_FOR_TRACY" => 1, "TRACY_PORT" => 9001) do
    Base.compilecache(pkg)
end
```

在这里，我们使用自定义端口来连接tracy，这使得在Tracy UI中更容易找到正确的客户端。

### Adding metadata to zones

各种 `jl_timing_show_*` 和 `jl_timing_printf` 函数可以用来将一个字符串（或多个字符串）附加到一个区域。例如，推理的跟踪区域显示正在推理的方法实例。

`TracyCZoneColor` 函数可用于设置某个区域的颜色。请在代码库中搜索以查看它是如何使用的。

### Viewing Tracy files in your browser

访问 https://topolarity.github.io/trace-viewer/ 以获取 Tracy 跟踪的（实验性）网页查看器。

您可以打开本地的 `.tracy` 文件或提供来自网络的 URL（例如，Github 仓库中的文件）。如果您从网络加载跟踪文件，您还可以直接与他人分享页面 URL，使他们能够查看相同的跟踪。

### Enabling stack trace samples

要在Tracy中启用调用栈采样，请在您的`Make.user`文件中使用以下选项构建Julia：

```
WITH_TRACY := 1
WITH_TRACY_CALLSTACKS := 1
USE_BINARYBUILDER_LIBTRACYCLIENT := 0
```

您可能还需要运行 `make -C deps clean-libtracyclient` 以强制重新构建 Tracy。

此功能对跟踪大小和分析开销有显著影响，因此建议在可能的情况下关闭调用栈采样，特别是如果您打算在线共享您的跟踪文件。

请注意，Julia JIT 运行时尚未集成 Tracy 的符号化，因此在这些堆栈跟踪中，Julia 函数通常会显示为未知。

## Intel VTune (ITTAPI) Profiler

*此部分尚未编写。*
