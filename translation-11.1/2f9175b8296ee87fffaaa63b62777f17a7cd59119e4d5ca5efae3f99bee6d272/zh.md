```
DEPOT_PATH
```

一个“仓库”位置的堆栈，包管理器以及 Julia 的代码加载机制在其中查找包注册表、已安装的包、命名环境、代码库克隆、缓存的编译包图像和配置文件。默认情况下，它包括：

1. `~/.julia`，其中 `~` 是系统上适当的用户主目录；
2. 一个特定于架构的共享系统目录，例如 `/usr/local/share/julia`；
3. 一个与架构无关的共享系统目录，例如 `/usr/share/julia`。

因此 `DEPOT_PATH` 可能是：

```julia
[joinpath(homedir(), ".julia"), "/usr/local/share/julia", "/usr/share/julia"]
```

第一个条目是“用户仓库”，应由当前用户可写并拥有。用户仓库是：注册表被克隆、新包版本被安装、命名环境被创建和更新、包代码库被克隆、新编译的包图像文件被保存、日志文件被写入、开发包默认被检出，以及全局配置数据被保存。仓库路径中的后续条目被视为只读，适合由系统管理员安装和管理的注册表、包等。

如果设置了 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 环境变量，则 `DEPOT_PATH` 会根据该变量填充。

## DEPOT_PATH 内容

`DEPOT_PATH` 中的每个条目都是指向一个目录的路径，该目录包含 Julia 用于各种目的的子目录。以下是仓库中可能存在的一些子目录的概述：

  * `artifacts`：包含包使用的内容，Pkg 管理其安装。
  * `clones`：包含包代码库的完整克隆。由 `Pkg.jl` 维护并用作缓存。
  * `config`：包含 Julia 级别的配置，例如 `startup.jl`
  * `compiled`：包含包的预编译 `*.ji` 文件。由 Julia 维护。
  * `dev`：`Pkg.develop` 的默认目录。由 `Pkg.jl` 和用户维护。
  * `environments`：默认包环境。例如，特定 Julia 版本的全局环境。由 `Pkg.jl` 维护。
  * `logs`：包含 `Pkg` 和 `REPL` 操作的日志。由 `Pkg.jl` 和 `Julia` 维护。
  * `packages`：包含包，其中一些是显式安装的，另一些是隐式依赖。由 `Pkg.jl` 维护。
  * `registries`：包含包注册表。默认情况下只有 `General`。由 `Pkg.jl` 维护。
  * `scratchspaces`：包含包本身通过 [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) 包安装的内容。`Pkg.gc()` 将删除已知未使用的内容。

!!! note
    想要存储内容的包应通过 [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) 使用 `scratchspaces` 子目录，而不是在仓库根目录中创建新的子目录。


另请参见 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 和 [代码加载](@ref code-loading)。
