# [Workflow Tips](@id man-workflow-tips)

以下是一些高效使用Julia的技巧。

## REPL-based workflow

正如在 [The Julia REPL](@ref) 中详细阐述的，Julia 的 REPL 提供了丰富的功能，便于高效的交互式工作流程。以下是一些可能进一步提升您在命令行体验的提示。

### A basic editor/REPL workflow

最基本的 Julia 工作流程涉及将文本编辑器与 `julia` 命令行结合使用。

创建一个文件，例如 `Tmp.jl`，并在其中包含

```julia
module Tmp

say_hello() = println("Hello!")

# Your other definitions here

end # module

using .Tmp
```

然后，在同一目录中，启动 Julia REPL（使用 `julia` 命令）。按如下方式运行新文件：

```
julia> include("Tmp.jl")

julia> Tmp.say_hello()
Hello!
```

在 REPL 中探索想法。将好的想法保存在 `Tmp.jl` 中。要在文件更改后重新加载它，只需再次 `include` 它。

上述的关键在于您的代码被封装在一个模块中。这使您可以编辑 `struct` 定义并删除方法，而无需重新启动 Julia。

（解释：`struct` 在定义后不能被编辑，也不能删除方法。但是你 *可以* 重写模块的定义，这就是我们在重新 `include("Tmp.jl")` 时所做的。）

此外，将代码封装在模块中可以保护它不受 REPL 中先前状态的影响，从而保护您免受难以检测的错误。

## Browser-based workflow

在浏览器中与 Julia 互动有几种方式：

  * 使用 Pluto 笔记本通过 [Pluto.jl](https://github.com/fonsp/Pluto.jl)
  * 使用 Jupyter 笔记本通过 [IJulia.jl](https://github.com/JuliaLang/IJulia.jl)

## Revise-based workflows

无论您是在 REPL 还是在 IJulia 中，您通常可以通过 [Revise](https://github.com/timholy/Revise.jl) 来改善您的开发体验。根据 [Revise documentation](https://timholy.github.io/Revise.jl/stable/) 中的说明，通常会配置 Revise 在每次启动 julia 时自动启动。一旦配置完成，Revise 将跟踪任何加载模块中的文件更改，以及通过 `includet` 加载到 REPL 中的任何文件（但不适用于普通的 `include`）；您可以编辑这些文件，所做的更改将立即生效，而无需重新启动您的 julia 会话。标准工作流程与上述基于 REPL 的工作流程类似，具有以下修改：

1. 将您的代码放在加载路径上的某个模块中。有几种实现此目的的选项，其中两个推荐的选择是：

      * 对于长期项目，请使用 [PkgTemplates](https://github.com/invenia/PkgTemplates.jl)：

        ```julia
        using PkgTemplates
        t = Template()
        t("MyPkg")
        ```

        这将会在你的 `.julia/dev` 目录中创建一个空的包，`"MyPkg"`。请注意，PkgTemplates 允许你通过其 `Template` 构造函数控制许多不同的选项。

        在下面的步骤2中，编辑 `MyPkg/src/MyPkg.jl` 以更改源代码，并编辑 `MyPkg/test/runtests.jl` 以进行测试。
      * 对于“临时”项目，您可以通过在临时目录中进行工作（例如，`/tmp`）来避免任何清理的需要。

        导航到您的临时目录并启动 Julia，然后执行以下操作：

        ```julia-repl
        pkg> generate MyPkg            # type ] to enter pkg mode
        julia> push!(LOAD_PATH, pwd())   # hit backspace to exit pkg mode
        ```

        如果您重新启动 Julia 会话，您将需要重新发出修改 `LOAD_PATH` 的命令。

        在下面的步骤2中，编辑 `MyPkg/src/MyPkg.jl` 以更改源代码，并创建您选择的任何测试文件。
2. 开发您的包裹

    *在* 加载任何代码之前，请确保您正在运行 Revise：输入 `using Revise` 或按照其文档配置以自动运行。

    然后导航到包含您的测试文件的目录（这里假设为 `"runtests.jl"`），并执行以下操作：

    ```julia-repl
    julia> using MyPkg

    julia> include("runtests.jl")
    ```

    您可以在编辑器中迭代地修改 MyPkg 中的代码，并使用 `include("runtests.jl")` 重新运行测试。通常，您不需要重新启动 Julia 会话就能看到更改生效（受限于一些 [limitations](https://timholy.github.io/Revise.jl/stable/limitations/)）。
