```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/NEWS.md"
```

# Julia v1.11 Release Notes

## New language features

  * 新的 `Memory` 类型提供了一个低级容器，作为 `Array` 的替代。`Memory` 的开销更小，构造速度更快，适合不需要 `Array` 所有功能（例如多维）的情况。现在大部分 `Array` 类型在 Julia 中是基于 `Memory` 实现的，这为多个函数（例如 `push!`）带来了显著的速度提升，并且使代码更易于维护（[#51319](https://github.com/JuliaLang/julia/issues/51319)）。
  * `public` 是一个新关键字。标记为 `public` 的符号被视为公共 API。标记为 `export` 的符号现在也被视为公共 API。`public` 和 `export` 之间的区别在于，当 `using` 一个包/模块时，`public` 名称不会变得可用 ([#50105](https://github.com/JuliaLang/julia/issues/50105))。
  * `ScopedValue` 实现了跨任务的动态作用域继承 ([#50958](https://github.com/JuliaLang/julia/issues/50958))。
  * `Manifest.toml` 文件现在可以重命名为 `Manifest-v{major}.{minor}.toml` 格式，以便被指定的 Julia 版本优先选择。即在同一文件夹中，`Manifest-v1.11.toml` 将被 v1.11 使用，而 `Manifest.toml` 将被其他所有 Julia 版本使用。这使得同时管理多个 Julia 版本的环境变得更加容易 ([#43845](https://github.com/JuliaLang/julia/issues/43845))。
  * 支持 Unicode 15.1 ([#51799](https://github.com/JuliaLang/julia/issues/51799))。

## Language changes

  * 在预编译期间，`atexit` 钩子现在在保存输出文件之前运行。这允许用户安全地拆除后台状态（例如关闭 `Timer` 和向心跳任务发送断开连接通知）以及在程序想要开始退出时清理其他资源。
  * Code coverage and malloc tracking is no longer generated during the package precompilation stage. Further, during these modes pkgimage caches are now used for packages that are not being tracked. This means that coverage testing (the default for `julia-actions/julia-runtest`) will by default use pkgimage caches for all other packages than the package being tested, likely meaning faster test execution ([#52123](https://github.com/JuliaLang/julia/issues/52123)).
  * 在 `JULIA_DEPOT_PATH` 中指定路径现在会导致空字符串的扩展，从而省略默认用户仓库 ([#51448](https://github.com/JuliaLang/julia/issues/51448))。
  * 预编译缓存文件现在可以重新定位，并且它们的有效性现在通过其源文件的内容哈希进行验证，而不是通过它们的 `mtime` ([#49866](https://github.com/JuliaLang/julia/issues/49866))。
  * 扩展现在可以依赖其他扩展，如果它们的触发器包含任何希望依赖的扩展的所有触发器（+ 至少一个其他触发器）。不满足此要求的扩展间依赖现在在预编译期间被阻止使用 `Base.get_extension`，以防止扩展循环 [#55557](https://github.com/JuliaLang/julia/issues/55557)。

## Compiler/Runtime improvements

  * 更新的 GC 启发式算法以计算分配的页面而不是单个对象 ([#50144](https://github.com/JuliaLang/julia/issues/50144))。
  * 添加了对代码块上注释 `Base.@assume_effects` 的支持 ([#52400](https://github.com/JuliaLang/julia/issues/52400))。

## Command-line option changes

  * The entry point for Julia has been standardized to `Main.main(args)`. This must be explicitly opted into using the `@main` macro (see the docstring for further details). When opted-in, and `julia` is invoked to run a script or expression (i.e. using `julia script.jl` or `julia -e expr`), `julia` will subsequently run the `Main.main` function automatically. This is intended to unify script and compilation workflows, where code loading may happen in the compiler and execution of `Main.main` may happen in the resulting executable. For interactive use, there is no semantic difference between defining a `main` function and executing the code directly at the end of the script ([#50974](https://github.com/JuliaLang/julia/issues/50974)).
  * `--compiled-modules` 和 `--pkgimages` 标志现在可以设置为 `existing`，这将导致 Julia 考虑加载现有的缓存文件，但不会创建新的文件（[#50586](https://github.com/JuliaLang/julia/issues/50586)，[#52573](https://github.com/JuliaLang/julia/issues/52573)）。
  * `--project` 参数现在接受 `@script`，以提供相对于传递的脚本文件的 Project.toml 目录路径。`--project=@script/foo` 用于 `foo` 子目录。如果在后面没有给出路径（即 `--project=@script`），那么（就像 `--project=@.` 一样）将搜索该目录及其父目录中的 Project.toml（[#50864](https://github.com/JuliaLang/julia/issues/50864) 和 [#53352](https://github.com/JuliaLang/julia/issues/53352)）

## Multi-threading changes

  * `Threads.@threads` 现在支持 `:greedy` 调度器，旨在处理非均匀工作负载 ([#52096](https://github.com/JuliaLang/julia/issues/52096))。
  * A new public (but unexported) struct `Base.Lockable{T, L<:AbstractLock}` makes it easy to bundle a resource and its lock together ([#52898](https://github.com/JuliaLang/julia/issues/52898)).

## Build system changes

  * 有一个新的 `Makefile` 用于使用基于配置的和链接时优化（PGO 和 LTO）策略构建 Julia 和 LLVM，详见 `contrib/pgo-lto/Makefile` ([#45641](https://github.com/JuliaLang/julia/issues/45641))。

## New library functions

  * 围绕“注释”(`Pair{Symbol, Any}` 条目，例如 `:lang => "en"` 或 `:face => :magenta`) 的三种新类型。这些注释在操作（例如字符串连接 `*`）中尽可能保留。

      * `AnnotatedString` 是一种新的 `AbstractString` 类型。它封装了一个底层字符串，并允许将注释附加到字符串的区域。该类型在新的 `StyledStrings` 标准库中被广泛使用，以保存样式信息。
      * `AnnotatedChar` 是一种新的 `AbstractChar` 类型。它包装了另一个字符，并持有适用于它的注释列表。
      * `AnnotatedIOBuffer` 是一种新的 `IO` 类型，它模仿 `IOBuffer`，但具有专门用于注释内容的 `read`/`write` 方法。这可以被视为某种“字符串构建器”，同时也是注释内容和未注释内容之间的粘合剂。
  * `in!(x, s::AbstractSet)` 将返回 `x` 是否在 `s` 中，如果不在，则将 `x` 插入 `s`（[#45156](https://github.com/JuliaLang/julia/issues/45156)，[#51636](https://github.com/JuliaLang/julia/issues/51636)）。
  * 新的 `Libc.mkfifo` 函数封装了 Unix 平台上的 `mkfifo` C 函数 ([#34587](https://github.com/JuliaLang/julia/issues/34587))。
  * `logrange(start, stop; length)` makes a range of constant ratio, instead of constant step ([#39071](https://github.com/JuliaLang/julia/issues/39071))
  * `copyuntil(out, io, delim)` 和 `copyline(out, io)` 将数据复制到 `out::IO` 流中 ([#48273](https://github.com/JuliaLang/julia/issues/48273))。
  * `eachrsplit(string, pattern)` 从右到左迭代分割子字符串 ([#51646](https://github.com/JuliaLang/julia/issues/51646))。
  * `Sys.username()` 可以用来返回当前用户的用户名 ([#51897](https://github.com/JuliaLang/julia/issues/51897))。
  * `Sys.isreadable(), Sys.iswritable()` 可用于检查当前用户是否具有允许读取和写入的访问权限。([#53320](https://github.com/JuliaLang/julia/issues/53320))
  * `GC.logging_enabled()` 可以用来测试是否通过 `GC.enable_logging` 启用了 GC 日志 ([#51647](https://github.com/JuliaLang/julia/issues/51647))。
  * `IdSet` 现在从 Base 导出并被视为公共 ([#53262](https://github.com/JuliaLang/julia/issues/53262))。
  * `@time` 现在报告任何锁冲突的计数，其中 `ReentrantLock` 必须等待，以及一个新的宏 `@lock_conflicts`，该宏返回该计数 ([#52883](https://github.com/JuliaLang/julia/issues/52883))。
  * 新的宏 `Base.Cartesian.@ncallkw` 类似于 `Base.Cartesian.@ncall`，但允许在函数调用中添加关键字参数 ([#51501](https://github.com/JuliaLang/julia/issues/51501))。
  * 新函数 `Docs.hasdoc(module, symbol)` 用于判断一个名称是否具有文档字符串 ([#52139](https://github.com/JuliaLang/julia/issues/52139))。
  * 新函数 `Docs.undocumented_names(module)` 返回模块的未文档化公共名称 ([#52413](https://github.com/JuliaLang/julia/issues/52413))。

## New library features

  * `invmod(n, T)` 其中 `T` 是一种原生整数类型，现在计算 `n` 在 `T` 定义的模整数环中的模逆 ([#52180](https://github.com/JuliaLang/julia/issues/52180))。
  * `invmod(n)` is an abbreviation for `invmod(n, typeof(n))` for native integer types ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `replace(string, pattern...)` 现在支持一个可选的 `IO` 参数，可以将输出写入流而不是返回字符串 ([#48625](https://github.com/JuliaLang/julia/issues/48625))。
  * 新的方法 `allequal(f, itr)` 和 `allunique(f, itr)` 接受一个谓词函数 ([#47679](https://github.com/JuliaLang/julia/issues/47679))。
  * `sizehint!(s, n)` 现在支持一个可选的 `shrink` 参数来禁用缩小 ([#51929](https://github.com/JuliaLang/julia/issues/51929))。
  * 将 `IOBuffer` 作为 `Process` spawn 的 stdout 参数现在按预期工作，与 `wait` 或 `success` 同步，因此在那里不再需要 `Base.BufferStream` 来确保正确性以避免数据竞争 ([#52461](https://github.com/JuliaLang/julia/issues/52461))。
  * 在进程退出后，`closewrite` 将不再自动调用传递给它的流。请改为在进程上调用 `wait` 以确保内容完全写入，然后手动调用 `closewrite` 以避免数据竞争，或者使用 `open` 的回调形式来自动处理所有这些 ([#52461](https://github.com/JuliaLang/julia/issues/52461))。
  * `@timed` 现在还额外返回编译和重新编译的耗时 ([#52889](https://github.com/JuliaLang/julia/issues/52889))。
  * `filter` 现在可以作用于 `NamedTuple` ([#50795](https://github.com/JuliaLang/julia/issues/50795))。
  * `Iterators.cycle(iter, n)` 在 `iter` 上运行固定次数，而不是无限次 ([#47354](https://github.com/JuliaLang/julia/issues/47354))。
  * `zero(::AbstractArray)` 现在递归应用，因此 `zero([[1,2],[3,4,5]])` 现在生成加法单位元 `[[0,0],[0,0,0]]` 而不是报错 ([#38064](https://github.com/JuliaLang/julia/issues/38064))。
  * `include_dependency(path; track_content=true)` 允许从使用 `mtime` 切换到对预编译依赖项的哈希，以恢复预编译缓存的可重定位性 ([#51798](https://github.com/JuliaLang/julia/issues/51798))。

## Standard library changes

  * 回退方法 `write(::IO, ::AbstractArray)` 现在递归调用 `write` 的每个元素，而是写入每个值的内存表示。例如，`write(io, 'a':'b')` 现在为每个字符写入 4 个字节，而不是写入每个字符的 UTF-8 表示。新格式与 `Array` 使用的格式兼容，使得可以使用 `read!` 将数据取回（[#42593](https://github.com/JuliaLang/julia/issues/42593)）。
  * 无法以一般一致的方式为有状态迭代器定义 `length`。通过删除 `length(::Stateful)` 方法，解决了有状态迭代器潜在的静默错误结果问题。`Stateful` 的最后一个类型参数也被删除。问题：([#47790](https://github.com/JuliaLang/julia/issues/47790))，PR: ([#51747](https://github.com/JuliaLang/julia/issues/51747))。

#### Package Manager

  * 现在可以在 Project.toml 中的 `[sources]` 部分为包指定“源”。这可以用于添加未注册的正常或测试依赖项。
  * Pkg 现在遵循 `[compat]` 边界对于 `julia` 的要求，并在运行的 Julia 二进制版本与 `Project.toml` 中的边界不兼容时引发错误。Pkg 在处理 Registry 包时一直遵循这一兼容性。这一变化主要影响本地包。
  * `pkg> add` 和 `Pkg.add` 现在将在活动环境是一个包（具有 `name` 和 `uuid` 条目）时，为新的直接依赖项添加兼容性条目。
  * 依赖项现在可以通过 `pkg> add --weak/extra Foo` 或 `Pkg.add("Foo", target=:weakdeps/:extras)` 形式直接添加为弱依赖或额外依赖。

#### StyledStrings

  * 一个新的标准库，用于以更全面和结构化的方式处理样式（[#49586](https://github.com/JuliaLang/julia/issues/49586)）。
  * 新的 `Faces` 结构体作为文本样式信息的容器（可以理解为字体、颜色和装饰），并提供了一个方便、可扩展（通过 `addface!`）和可定制（使用用户的 `Faces.toml` 和 `loadfaces!`）的样式内容框架（[#49586](https://github.com/JuliaLang/julia/issues/49586)）。
  * 新的 `@styled_str` 字符串宏提供了一种方便的方法来创建带有各种样式或其他属性的 `AnnotatedString`（[#49586](https://github.com/JuliaLang/julia/issues/49586)）。

#### Libdl

  * 一个新的 `LazyLibrary` 类型从 `Libdl` 导出，用于构建链式懒加载库，主要用于 JLLs ([#50074](https://github.com/JuliaLang/julia/issues/50074))。

#### LinearAlgebra

  * `cbrt(::AbstractMatrix{<:Real})` 现在已定义，并返回实值矩阵的实值立方根（[#50661](https://github.com/JuliaLang/julia/issues/50661)）。
  * `eigvals/eigen(A, bunchkaufman(B))` and `eigvals/eigen(A, lu(B))`, which utilize the Bunchkaufman (LDL) and LU decomposition of `B`,  respectively, now efficiently compute the generalized eigenvalues (`eigen`: and eigenvectors) of `A` and `B`. Note: The second  argument is the output of `bunchkaufman` or `lu` ([#50471](https://github.com/JuliaLang/julia/issues/50471)).
  * 现在有一个专门的调度用于 `eigvals/eigen(::Hermitian{<:Tridiagonal})`，它执行相似变换以创建一个实对称的三对角矩阵，并使用 LAPACK 例程解决该矩阵（[#49546](https://github.com/JuliaLang/julia/issues/49546)）。
  * 结构化矩阵现在保留父矩阵的轴（对于 `Symmetric`/`Hermitian`/`AbstractTriangular`/`UpperHessenberg`），或者主对角线的轴（对于带状矩阵） ([#52480](https://github.com/JuliaLang/julia/issues/52480))。
  * `bunchkaufman` 和 `bunchkaufman!` 现在适用于任何 `AbstractFloat`、`Rational` 及其复数变体。`bunchkaufman` 现在支持 `Integer` 类型，通过内部转换为 `Rational{BigInt}`。新增函数 `inertia`，用于计算由 `BunchKaufman` 分解对象给出的实对称或厄米矩阵的对角因子的惯性。对于复对称矩阵，`inertia` 仅计算对角因子的零特征值的数量 ([#51487](https://github.com/JuliaLang/julia/issues/51487))。
  * Packages that specialize matrix-matrix `mul!` with a method signature of the form `mul!(::AbstractMatrix, ::MyMatrix, ::AbstractMatrix, ::Number, ::Number)` no longer encounter method ambiguities when interacting with `LinearAlgebra`. Previously, ambiguities used to arise when multiplying a `MyMatrix` with a structured matrix type provided by LinearAlgebra, such as `AbstractTriangular`, which used to necessitate additional methods to resolve such ambiguities. Similar sources of ambiguities have also been removed for matrix-vector `mul!` operations ([#52837](https://github.com/JuliaLang/julia/issues/52837)).
  * `lu` 和 `issuccess(::LU)` 现在接受一个 `allowsingular` 关键字参数。当设置为 `true` 时，具有秩缺陷的 U 因子的有效分解将被视为成功，而不是抛出错误。这种分解现在通过打印因子以及 "rank-deficient" 注释来显示，而不是打印 "Failed Factorization" 消息 ([#52957](https://github.com/JuliaLang/julia/issues/52957))。

#### Random

  * `rand` 现在支持对 `Tuple` 类型进行采样 ([#35856](https://github.com/JuliaLang/julia/issues/35856), [#50251](https://github.com/JuliaLang/julia/issues/50251))。
  * `rand` 现在支持对 `Pair` 类型进行采样 ([#28705](https://github.com/JuliaLang/julia/issues/28705))。
  * 当使用 `Random` 提供的随机数生成器（RNG）进行播种时，现在可以使用负整数种子（[#51416](https://github.com/JuliaLang/julia/issues/51416)）。
  * 可种子随机数生成器来自 `Random` 现在可以通过字符串进行种子设置，例如 `seed!(rng, "a random seed")` ([#51527](https://github.com/JuliaLang/julia/issues/51527))。

#### REPL

  * Tab 完成提示现在在 REPL 中输入时以较浅的文本显示。要禁用此功能，请在交互式环境中设置 `Base.active_repl.options.hint_tab_completes = false`，或在 startup.jl 中设置：

    ```
    if VERSION >= v"1.11.0-0"
      atreplinit() do repl
          repl.options.hint_tab_completes = false
      end
    end
    ```

    ([#51229](https://github.com/JuliaLang/julia/issues/51229)).
  * Meta-M 现在在空提示下切换上下文模块，介于之前的非主上下文模块和主模块之间，以便于简单地来回切换（[#51616](https://github.com/JuliaLang/julia/issues/51616)，[#52670](https://github.com/JuliaLang/julia/issues/52670)）。

#### Dates

未记录的函数 `adjust` 不再导出，但现在已被记录（[#53092](https://github.com/JuliaLang/julia/issues/53092)）。

#### Statistics

  * 统计现在是一个可升级的标准库 ([#46501](https://github.com/JuliaLang/julia/issues/46501))。

#### Distributed

  * `pmap` 现在默认使用 `CachingPool` ([#33892](https://github.com/JuliaLang/julia/issues/33892))。

## Deprecated or removed

  * `Base.map`、`Iterators.map` 和 `foreach` 失去了它们的单参数方法（[#52631](https://github.com/JuliaLang/julia/issues/52631)）。

## External dependencies

  * libuv 库已从 v1.44.2 更新到 v1.48.0 ([#49937](https://github.com/JuliaLang/julia/issues/49937))。
  * `tput` 不再被调用来检查终端能力；它已被一个纯 Julia 的 terminfo 解析器替代（[#50797](https://github.com/JuliaLang/julia/issues/50797)）。
  * 终端信息数据库 `terminfo` 现在默认被包含在内，当系统上没有 `terminfo` 时，提供了更好的 REPL 用户体验。可以使用 Makefile 选项 `WITH_TERMINFO=0` 在不包含数据库的情况下构建 Julia。 ([#55411](https://github.com/JuliaLang/julia/issues/55411))

## Tooling Improvements

  * CI 现在对所有 PR 执行有限的自动拼写错误检测。如果您合并一个拼写错误 CI 检查失败的 PR，那么在未来对编辑那些相同文件的 PR 的 CI 运行中，报告的拼写错误将被自动忽略 ([#51704](https://github.com/JuliaLang/julia/issues/51704))。
