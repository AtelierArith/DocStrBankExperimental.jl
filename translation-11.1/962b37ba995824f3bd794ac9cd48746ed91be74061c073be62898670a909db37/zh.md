# Fixing precompilation hangs due to open tasks or IO

在 Julia 1.10 或更高版本中，您可能会看到以下消息：

![预编译挂起的截图](./img/precompilation_hang.png)

这可能会重复。如果它继续重复而没有任何提示表明它会自行解决，您可能遇到了需要修复的“预编译挂起”问题。即使它是暂时的，您可能更希望解决它，以便用户不会受到此警告的困扰。 本页面将指导您如何分析和修复此类问题。

如果您遵循建议并按下 `Ctrl-C`，您可能会看到

```
^C Interrupted: Exiting precompilation...

  1 dependency had warnings during precompilation:
┌ Test1 [ac89d554-e2ba-40bc-bc5c-de68b658c982]
│  [pid 2745] waiting for IO to finish:
│   Handle type        uv_handle_t->data
│   timer              0x55580decd1e0->0x7f94c3a4c340
```

此消息传达了两个关键信息：

  * 在 `Test2`（我们尝试使用的包）的依赖项 `Test1` 的预编译过程中发生了挂起。
  * 在 `Test1` 的预编译过程中，Julia 创建了一个 `Timer` 对象（如果你不熟悉定时器，可以使用 `?Timer`），该对象仍然处于打开状态；在它关闭之前，进程会挂起。

如果这对你来说足够提示你如何创建 `timer = Timer(args...)`，一个好的解决方案是在模块的最终 `end` 之前添加 `wait(timer)`，如果 `timer` 最终会自行完成，或者在你需要强制关闭它时使用 `close(timer)`。

然而，有些情况可能并不那么简单。通常，最佳的选择是首先确定挂起是由于 Test1 中的代码还是由于 Test1 的某个依赖项：

  * 选项 1： `Pkg.add("Aqua")` 并使用 [`Aqua.test_persistent_tasks`](https://juliatesting.github.io/Aqua.jl/dev/#Aqua.test_persistent_tasks-Tuple{Base.PkgId})。这应该帮助你识别出哪个包导致了问题，之后应遵循指令 [below](@ref pchang_fix)。如有需要，你可以创建一个 `PkgId`，格式为 `Base.PkgId(UUID("..."), "Test1")`，其中 `...` 来自 `Test1/Project.toml` 中的 `uuid` 条目。
  * 选项 2：手动诊断挂起的来源。

手动诊断：

1. `Pkg.develop("Test1")`
2. Comment out all the code `include`d or defined in `Test1`, *except* the `using/import` statements.
3. 尝试再次 `using Test2`（或者甚至 `using Test1` 假设那也会挂起）

现在我们来到了一个分岔路口：要么

  * 挂起仍然存在，表明它是 [due to one of your dependencies](@ref pchang_deps)
  * 挂件消失，表明它是 [due to something in your code](@ref pchang_fix)。

## [Diagnosing and fixing hangs due to a package dependency](@id pchang_deps)

使用二分查找来识别有问题的依赖项：首先注释掉一半的依赖项，然后当你确定是哪个部分有问题时，再注释掉那一半中的一半，依此类推。（你不必将它们从项目中移除，只需注释掉 `using`/`import` 语句。）

一旦你确定了一个可疑包（在这里我们称之为 `ThePackageYouThinkIsCausingTheProblem`），首先尝试对该包进行预编译。如果在预编译过程中也出现挂起，继续向后追踪问题。

然而，最有可能的是 `ThePackageYouThinkIsCausingTheProblem` 会正常预编译。这表明问题出在函数 `ThePackageYouThinkIsCausingTheProblem.__init__` 中，该函数在 `ThePackageYouThinkIsCausingTheProblem` 的预编译期间不会运行，但在任何加载 `ThePackageYouThinkIsCausingTheProblem` 的包中会运行。为了验证这个理论，设置一个最小工作示例（MWE），类似于

```julia
(@v1.10) pkg> generate MWE
  Generating  project MWE:
    MWE\Project.toml
    MWE\src\MWE.jl
```

`MWE.jl` 的源代码在哪里

```julia
module MWE
using ThePackageYouThinkIsCausingTheProblem
end
```

并且您已将 `ThePackageYouThinkIsCausingTheProblem` 添加到 MWE 的依赖项中。

如果该最小可重现示例（MWE）重现了挂起问题，那么你找到了罪魁祸首：`ThePackageYouThinkIsCausingTheProblem.__init__` 必须在创建 `Timer` 对象。如果定时器对象可以安全地 `close`，那是一个不错的选择。否则，最常见的解决方案是在 *任何* 包被预编译时避免创建定时器：添加

```julia
ccall(:jl_generating_output, Cint, ()) == 1 && return nothing
```

作为 `ThePackageYouThinkIsCausingTheProblem.__init__` 的第一行，它将避免在任何旨在预编译包的 Julia 进程中进行任何初始化。

## [Fixing package code to avoid hangs](@id pchang_fix)

搜索您的包以查找暗示性词汇（这里像“计时器”），并查看您是否可以识别出问题产生的位置。请注意，像这样的*定义*方法

```julia
maketimer() = Timer(timer -> println("hi"), 0; interval=1)
```

本身并不成问题：只有在模块被定义时调用 `maketimer` 时，它才会导致这个问题。这可能是由于顶层语句引起的，例如

```julia
const GLOBAL_TIMER = maketimer()
```

或者它可能在一个 [precompile workload](https://github.com/JuliaLang/PrecompileTools.jl) 中发生。

如果你在识别因果关系时遇到困难，可以考虑进行二分查找：注释掉你包中的部分内容（或 `include` 行以省略整个文件），直到你缩小问题的范围。
