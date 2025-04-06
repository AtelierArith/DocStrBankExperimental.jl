```
LOAD_PATH
```

一个路径数组，用于在加载代码时考虑作为项目环境或包目录的 `using` 和 `import` 语句。它根据 [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) 环境变量的设置进行填充；否则默认为 `["@", "@v#.#", "@stdlib"]`。以 `@` 开头的条目具有特殊含义：

  * `@` 指的是“当前活动环境”，其初始值最初由 [`JULIA_PROJECT`](@ref JULIA_PROJECT) 环境变量或 `--project` 命令行选项确定。
  * `@stdlib` 展开为当前 Julia 安装的标准库目录的绝对路径。
  * `@name` 指的是一个命名环境，这些环境存储在仓库中（参见 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)）的 `environments` 子目录下。用户的命名环境存储在 `~/.julia/environments` 中，因此如果存在并包含 `Project.toml` 文件，`@name` 将指向 `~/.julia/environments/name` 中的环境。如果 `name` 包含 `#` 字符，则它们将被 Julia 版本号的主、次和修订组件替换。例如，如果您正在运行 Julia 1.2，则 `@v#.#` 展开为 `@v1.2`，并将查找该名称的环境，通常位于 `~/.julia/environments/v1.2`。

可以通过调用 `Base.load_path()` 函数查看搜索项目和包的 `LOAD_PATH` 的完全展开值。

另请参见 [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH)，[`JULIA_PROJECT`](@ref JULIA_PROJECT)，[`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 和 [代码加载](@ref code-loading)。
