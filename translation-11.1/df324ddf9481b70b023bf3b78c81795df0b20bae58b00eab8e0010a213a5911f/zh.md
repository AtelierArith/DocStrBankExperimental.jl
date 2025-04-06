# [Code Loading](@id code-loading)

!!! note
    本章涵盖了包加载的技术细节。要安装包，请使用 [`Pkg`](@ref Pkg)，这是 Julia 内置的包管理器，用于将包添加到您的活动环境中。要使用您活动环境中已经存在的包，请写 `import X` 或 `using X`，如 [Modules documentation](@ref modules) 中所述。


## Definitions

Julia 有两种加载代码的机制：

1. **代码包含：** 例如 `include("source.jl")`。包含允许您将单个程序分割到多个源文件中。表达式 `include("source.jl")` 会导致文件 `source.jl` 的内容在发生 `include` 调用的模块的全局作用域中被评估。如果多次调用 `include("source.jl")`，则 `source.jl` 会被多次评估。包含的路径 `source.jl` 是相对于发生 `include` 调用的文件进行解释的。这使得重新定位源文件的子树变得简单。在 REPL 中，包含的路径是相对于当前工作目录进行解释的，[`pwd()`](@ref)。
2. **包加载：** 例如 `import X` 或 `using X`。导入机制允许您加载一个包——即一个独立的、可重用的 Julia 代码集合，封装在一个模块中——并使得结果模块在导入模块内部以名称 `X` 可用。如果在同一个 Julia 会话中多次导入相同的 `X` 包，它只会在第一次加载——在后续的导入中，导入模块会获得对同一模块的引用。不过，请注意，`import X` 可以在不同的上下文中加载不同的包：`X` 可以在主项目中指代一个名为 `X` 的包，但在每个依赖项中也可能指代不同的同名包。更多内容如下。

代码包含非常简单明了：它在调用者的上下文中评估给定的源文件。包加载建立在代码包含之上，并服务于 [different purpose](@ref modules)。本章的其余部分将重点讨论包加载的行为和机制。

一个 *包* 是一个具有标准布局的源树，提供可以被其他 Julia 项目重用的功能。通过 `import X` 或 `using X` 语句加载一个包。这些语句还使得名为 `X` 的模块——这是加载包代码的结果——在发生导入语句的模块中可用。在 `import X` 中，`X` 的含义是依赖于上下文的：加载哪个 `X` 包取决于语句发生的代码。因此，`import X` 的处理分为两个阶段：首先，它确定在此上下文中定义为 `X` 的 **是什么** 包；其次，它确定该特定的 `X` 包 **在哪里** 被找到。

这些问题通过在 [`LOAD_PATH`](@ref) 中列出的项目环境中搜索项目文件（`Project.toml` 或 `JuliaProject.toml`）、清单文件（`Manifest.toml` 或 `JuliaManifest.toml`，或以 `-v{major}.{minor}.toml` 作为特定版本后缀的同名文件），或源文件夹来回答。

## Federation of packages

大多数情况下，一个包可以仅通过其名称唯一识别。然而，有时一个项目可能会遇到需要使用两个不同包的情况，而这两个包共享相同的名称。虽然你可能能够通过重命名其中一个包来解决这个问题，但在一个大型共享代码库中被迫这样做可能会非常具有破坏性。相反，Julia 的代码加载机制允许相同的包名称在应用程序的不同组件中引用不同的包。

Julia 支持联邦包管理，这意味着多个独立方可以维护公共和私有包及包注册表，项目可以依赖来自不同注册表的公共和私有包的混合。来自各种注册表的包使用一套通用的工具和工作流程进行安装和管理。随 Julia 一起提供的 `Pkg` 包管理器让您可以安装和管理项目的依赖项。它帮助创建和操作项目文件（描述您的项目依赖于哪些其他项目）和清单文件（快照您项目完整依赖图的确切版本）。

联邦的一个后果是无法存在一个中央权威来进行包命名。不同的实体可能会使用相同的名称来指代无关的包。这种可能性是不可避免的，因为这些实体并不协调，甚至可能互不知晓。由于缺乏中央命名权威，单个项目可能最终依赖于具有相同名称的不同包。Julia 的包加载机制并不要求包名称在全局范围内是唯一的，即使在单个项目的依赖图中也是如此。相反，包是通过 [universally unique identifiers](https://en.wikipedia.org/wiki/Universally_unique_identifier)（UUID）来识别的，这些 UUID 在每个包创建时分配。通常你不需要直接处理这些有些繁琐的 128 位标识符，因为 `Pkg` 会为你生成和跟踪它们。然而，这些 UUID 提供了对 *“`X` 指的是什么包？”* 这个问题的明确答案。

由于去中心化命名问题有些抽象，逐步通过一个具体场景来理解这个问题可能会有所帮助。假设你正在开发一个名为 `App` 的应用程序，它使用两个包：`Pub` 和 `Priv`。`Priv` 是你创建的私有包，而 `Pub` 是你使用但不控制的公共包。当你创建 `Priv` 时，没有名为 `Priv` 的公共包。然而，随后一个不相关的名为 `Priv` 的包被发布并变得流行。事实上，`Pub` 包已经开始使用它。因此，当你下次升级 `Pub` 以获取最新的错误修复和功能时，`App` 将最终依赖于两个不同的名为 `Priv` 的包——这并不是因为你的任何操作，而仅仅是因为升级。`App` 直接依赖于你的私有 `Priv` 包，并且通过 `Pub` 间接依赖于新的公共 `Priv` 包。由于这两个 `Priv` 包是不同的，但都需要 `App` 正常工作，因此表达式 `import Priv` 必须根据它出现在 `App` 的代码中还是在 `Pub` 的代码中而引用不同的 `Priv` 包。为了处理这个问题，Julia 的包加载机制通过它们的 UUID 区分这两个 `Priv` 包，并根据其上下文（调用 `import` 的模块）选择正确的一个。这个区分是如何工作的由环境决定，如以下章节所解释的。

## Environments

一个 *环境* 决定了在各种代码上下文中 `import X` 和 `using X` 的含义，以及这些语句导致加载哪些文件。Julia 理解两种类型的环境：

1. **项目环境**是一个包含项目文件和可选清单文件的目录，形成一个*显式环境*。项目文件确定项目的直接依赖项的名称和身份。清单文件（如果存在）提供完整的依赖关系图，包括所有直接和间接依赖项、每个依赖项的确切版本，以及足够的信息以定位和加载正确的版本。
2. **包目录**是一个包含一组包的源树作为子目录的目录，并形成一个*隐式环境*。如果`X`是包目录的一个子目录，并且`X/src/X.jl`存在，那么包`X`在包目录环境中可用，`X/src/X.jl`是加载它的源文件。

这些可以混合在一起创建**一个堆叠环境**：一组有序的项目环境和包目录，叠加在一起形成一个单一的复合环境。优先级和可见性规则随后结合起来确定哪些包是可用的以及它们从哪里加载。例如，Julia 的加载路径形成了一个堆叠环境。

这些环境各自有不同的用途：

  * 项目环境提供**可重现性**。通过将项目环境检查到版本控制中——例如，一个 git 仓库——以及项目的其余源代码，您可以重现项目及其所有依赖项的确切状态。清单文件，特别是，捕获每个依赖项的确切版本，通过其源树的加密哈希进行识别，这使得 `Pkg` 能够检索正确的版本，并确保您正在运行为所有依赖项记录的确切代码。
  * 包目录提供了**便利**，当不需要一个完整的、经过仔细跟踪的项目环境时，它们非常有用。当你想将一组包放在某个地方并能够直接使用它们，而不需要为它们创建一个项目环境时，它们就显得尤为重要。
  * 堆叠环境允许**添加**工具到主环境。您可以将开发工具的环境推送到堆栈的末尾，以便从 REPL 和脚本中使用，但不能从包内部使用。

在高层次上，每个环境概念上定义了三张地图：根、图和路径。在解析 `import X` 的含义时，根和图地图用于确定 `X` 的身份，而路径地图用于定位 `X` 的源代码。这三张地图的具体角色是：

  * **根:** `name::Symbol` ⟶ `uuid::UUID`

    环境的根映射将包名称分配给 UUID，以便为环境提供给主项目的所有顶级依赖项（即可以在 `Main` 中加载的那些）。当 Julia 在主项目中遇到 `import X` 时，它会将 `X` 的身份查找为 `roots[:X]`。
  * **图:** `context::UUID` ⟶ `name::Symbol` ⟶ `uuid::UUID`

    环境的图是一个多层次的地图，它为每个 `context` UUID 分配一个从名称到 UUID 的映射，类似于根映射，但特定于该 `context`。当 Julia 在 UUID 为 `context` 的包的代码中看到 `import X` 时，它会查找 `X` 的身份为 `graph[context][:X]`。特别是，这意味着 `import X` 可以根据 `context` 引用不同的包。
  * **路径：** `uuid::UUID` × `name::Symbol` ⟶ `path::String`

    路径映射将每个包的 UUID-名称对分配到该包的入口点源文件的位置。在 `import X` 中 `X` 的身份通过根或图（取决于它是从主项目还是依赖项加载）解析为 UUID 后，Julia 通过在环境中查找 `paths[uuid,:X]` 来确定加载哪个文件以获取 `X`。包含此文件应该定义一个名为 `X` 的模块。一旦加载了此包，任何后续解析到相同 `uuid` 的导入将创建对已加载包模块的新绑定。

每种环境对这三种地图的定义各不相同，具体细节见以下各节。

!!! note
    为了便于理解，本章中的示例展示了根、图和路径的完整数据结构。然而，Julia 的包加载代码并没有显式地创建这些结构。相反，它仅在需要加载特定包时，懒惰地计算每个结构所需的部分。


### Project environments

项目环境由一个包含名为 `Project.toml` 的项目文件的目录确定，此外还可以选择性地包含一个名为 `Manifest.toml` 的清单文件。这些文件也可以被称为 `JuliaProject.toml` 和 `JuliaManifest.toml`，在这种情况下，`Project.toml` 和 `Manifest.toml` 将被忽略。这允许与其他可能认为名为 `Project.toml` 和 `Manifest.toml` 的文件重要的工具共存。然而，对于纯 Julia 项目，`Project.toml` 和 `Manifest.toml` 的名称是首选的。然而，从 Julia v1.10.8 开始，`(Julia)Manifest-v{major}.{minor}.toml` 被识别为一种格式，使得特定的 Julia 版本使用特定的清单文件，即在同一文件夹中，`Manifest-v1.11.toml` 将被 v1.11 使用，而 `Manifest.toml` 将被任何其他 Julia 版本使用。

项目环境的根、图形和路径图定义如下：

**环境的根映射**由项目文件的内容决定，特别是其顶层的 `name` 和 `uuid` 条目以及其 `[deps]` 部分（均为可选）。考虑以下假设应用程序 `App` 的示例项目文件，如前所述：

```toml
name = "App"
uuid = "8f986787-14fe-4607-ba5d-fbff2944afa9"

[deps]
Priv = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
Pub  = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
```

该项目文件暗示了以下根映射，如果它由一个 Julia 字典表示：

```julia
roots = Dict(
    :App  => UUID("8f986787-14fe-4607-ba5d-fbff2944afa9"),
    :Priv => UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"),
    :Pub  => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
)
```

根据这个根映射，在 `App` 的代码中，语句 `import Priv` 将导致 Julia 查找 `roots[:Priv]`，这将返回 `ba13f791-ae1d-465a-978b-69c3ad90f72b`，这是要在该上下文中加载的 `Priv` 包的 UUID。这个 UUID 确定了在主应用程序评估 `import Priv` 时要加载和使用哪个 `Priv` 包。

**项目环境的依赖图**由清单文件的内容决定（如果存在）。如果没有清单文件，则图为空。清单文件为每个项目的直接或间接依赖项包含一个节。对于每个依赖项，该文件列出了包的 UUID 和源树哈希或源代码的显式路径。考虑以下 `App` 的示例清单文件：

```toml
[[Priv]] # the private one
deps = ["Pub", "Zebra"]
uuid = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
path = "deps/Priv"

[[Priv]] # the public one
uuid = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
git-tree-sha1 = "1bf63d3be994fe83456a03b874b409cfd59a6373"
version = "0.1.5"

[[Pub]]
uuid = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
git-tree-sha1 = "9ebd50e2b0dd1e110e842df3b433cb5869b0dd38"
version = "2.1.4"

  [Pub.deps]
  Priv = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
  Zebra = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"

[[Zebra]]
uuid = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"
git-tree-sha1 = "e808e36a5d7173974b90a15a353b564f3494092f"
version = "3.4.2"
```

此清单文件描述了 `App` 项目的一个可能的完整依赖关系图：

  * 有两个不同的名为 `Priv` 的包被应用程序使用。它使用一个私有包，这是一个根依赖项，以及一个公共包，这是通过 `Pub` 的间接依赖项。它们通过各自不同的 UUID 进行区分，并且它们有不同的依赖：

      * 私有的 `Priv` 依赖于 `Pub` 和 `Zebra` 包。
      * 公共 `Priv` 没有依赖。
  * 该应用程序还依赖于 `Pub` 包，而 `Pub` 包又依赖于公共的 `Priv` 和与私有 `Priv` 包相同的 `Zebra` 包。

这个作为字典表示的依赖图，看起来像这样：

```julia
graph = Dict(
    # Priv – the private one:
    UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b") => Dict(
        :Pub   => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Priv – the public one:
    UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c") => Dict(),
    # Pub:
    UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1") => Dict(
        :Priv  => UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Zebra:
    UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62") => Dict(),
)
```

给定这个依赖关系 `graph`，当 Julia 在 UUID 为 `c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1` 的 `Pub` 包中看到 `import Priv` 时，它会查找：

```julia
graph[UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1")][:Priv]
```

并获取 `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`，这表明在 `Pub` 包的上下文中，`import Priv` 指的是公共的 `Priv` 包，而不是应用程序直接依赖的私有包。这就是为什么名称 `Priv` 在主项目中可以指代与其某个包的依赖项中不同的包，这允许在包生态系统中存在重复的名称。

如果在主 `App` 代码库中评估 `import Zebra` 会发生什么？由于 `Zebra` 并未出现在项目文件中，因此导入将失败，即使 `Zebra` *确实* 出现在清单文件中。此外，如果在公共 `Priv` 包中发生 `import Zebra`——该包的 UUID 为 `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`——那么也会失败，因为该 `Priv` 包在清单文件中没有声明的依赖项，因此无法加载任何包。`Zebra` 包只能被作为清单文件中显式依赖项的包加载：`Pub` 包和其中一个 `Priv` 包。

**项目环境的路径图** 从清单文件中提取。包 `uuid` 名为 `X` 的路径由以下规则（按顺序）确定：

1. 如果目录中的项目文件与 `uuid` 和名称 `X` 匹配，则可以：

      * 它有一个顶级的 `path` 条目，然后 `uuid` 将被映射到该路径，解释为相对于包含项目文件的目录。
      * 否则，`uuid` 被映射到相对于包含项目文件的目录的 `src/X.jl`。
2. 如果上述情况不成立，并且项目文件有一个相应的清单文件，并且清单中包含与 `uuid` 匹配的节，则：

      * 如果它有一个 `path` 条目，请使用该路径（相对于包含清单文件的目录）。
      * 如果它有一个 `git-tree-sha1` 条目，计算 `uuid` 和 `git-tree-sha1` 的确定性哈希函数——称之为 `slug`——并在 Julia `DEPOT_PATH` 全局数组中的每个目录中查找名为 `packages/X/$slug` 的目录。使用第一个存在的此类目录。

如果这些结果中的任何一个成功，源代码入口点的路径将是该结果，或者是该结果的相对路径加上 `src/X.jl`；否则，`uuid` 将没有路径映射。在加载 `X` 时，如果未找到源代码路径，查找将失败，用户可能会被提示安装适当的包版本或采取其他纠正措施（例如，将 `X` 声明为依赖项）。

在上面的示例清单文件中，要找到第一个 `Priv` 包的路径——即 UUID 为 `ba13f791-ae1d-465a-978b-69c3ad90f72b` 的那个——Julia 会在清单文件中查找其节，看到它有一个 `path` 条目，查看相对于 `App` 项目目录的 `deps/Priv`——假设 `App` 代码位于 `/home/me/projects/App`——看到 `/home/me/projects/App/deps/Priv` 存在，因此从那里加载 `Priv`。

如果另一方面，Julia 正在加载 *另一个* `Priv` 包——UUID 为 `2d15fe94-a1f7-436c-a4d8-07a9a496e01c` 的那个——它会在清单中找到它的节，看到它没有 `path` 条目，但有一个 `git-tree-sha1` 条目。然后，它计算这个 UUID/SHA-1 对的 `slug`，即 `HDkrT`（这个计算的具体细节并不重要，但它是一致且确定的）。这意味着这个 `Priv` 包的路径将在某个包仓库中为 `packages/Priv/HDkrT/src/Priv.jl`。假设 `DEPOT_PATH` 的内容是 `["/home/me/.julia", "/usr/local/julia"]`，那么 Julia 将查看以下路径以确认它们是否存在：

1. `/home/me/.julia/packages/Priv/HDkrT`
2. `/usr/local/julia/packages/Priv/HDkrT`

Julia 使用第一个存在的文件来尝试从找到的仓库中加载公共 `Priv` 包，该文件位于 `packages/Priv/HDKrT/src/Priv.jl`。

这是我们示例 `App` 项目环境的可能路径图的表示，如上文中提供的清单所示，经过在本地文件系统中搜索后得到的依赖关系图：

```julia
paths = Dict(
    # Priv – the private one:
    (UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"), :Priv) =>
        # relative entry-point inside `App` repo:
        "/home/me/projects/App/deps/Priv/src/Priv.jl",
    # Priv – the public one:
    (UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"), :Priv) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Priv/HDkr/src/Priv.jl",
    # Pub:
    (UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"), :Pub) =>
        # package installed in the user depot:
        "/home/me/.julia/packages/Pub/oKpw/src/Pub.jl",
    # Zebra:
    (UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"), :Zebra) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Zebra/me9k/src/Zebra.jl",
)
```

此示例地图包含三种不同类型的包位置（第一和第三个是默认加载路径的一部分）：

1. 私有 `Priv` 包是 "[vendored](https://stackoverflow.com/a/35109534)" 在 `App` 仓库中。
2. 公共的 `Priv` 和 `Zebra` 包在系统仓库中，系统管理员安装和管理的包都存放在这里。这些包对系统上的所有用户都是可用的。
3. `Pub` 包位于用户仓库中，用户安装的包都存放在这里。这些包仅对安装它们的用户可用。

### Package directories

包目录提供了一种更简单的环境，但无法处理名称冲突。在包目录中，顶级包的集合是“看起来像”包的子目录集合。如果目录包含以下任一“入口点”文件，则包 `X` 存在于包目录中：

  * `X.jl`
  * `X/src/X.jl`
  * `X.jl/src/X.jl`

一个包目录中的包可以导入哪些依赖项取决于该包是否包含项目文件：

  * 如果它有一个项目文件，则只能导入项目文件的 `[deps]` 部分中标识的那些包。
  * 如果没有项目文件，它可以导入任何顶级包——即可以在 `Main` 或 REPL 中加载的相同包。

**根映射**是通过检查包目录的内容来生成所有存在的包的列表。此外，将为每个条目分配一个UUID，如下所示：对于在文件夹`X`中找到的给定包...

1. 如果 `X/Project.toml` 存在并且有一个 `uuid` 条目，则 `uuid` 是该值。
2. 如果 `X/Project.toml` 存在但没有顶层 UUID 条目，则 `uuid` 是通过对 `X/Project.toml` 的规范（真实）路径进行哈希生成的虚拟 UUID。
3. 否则（如果 `Project.toml` 不存在），那么 `uuid` 是全零的 [nil UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier#Nil_UUID)。

**项目目录的依赖图**由每个包的子目录中项目文件的存在和内容决定。规则如下：

  * 如果一个包子目录没有项目文件，那么它将被从图中省略，并且其代码中的导入语句将被视为顶级，与主项目和 REPL 相同。
  * 如果一个包子目录有一个项目文件，那么其 UUID 的图形条目就是项目文件的 `[deps]` 映射，如果该部分缺失，则视为为空。

作为示例，假设一个包目录具有以下结构和内容：

```
Aardvark/
    src/Aardvark.jl:
        import Bobcat
        import Cobra

Bobcat/
    Project.toml:
        [deps]
        Cobra = "4725e24d-f727-424b-bca0-c4307a3456fa"
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Bobcat.jl:
        import Cobra
        import Dingo

Cobra/
    Project.toml:
        uuid = "4725e24d-f727-424b-bca0-c4307a3456fa"
        [deps]
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Cobra.jl:
        import Dingo

Dingo/
    Project.toml:
        uuid = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Dingo.jl:
        # no imports
```

这里是一个对应的根结构，以字典形式表示：

```julia
roots = Dict(
    :Aardvark => UUID("00000000-0000-0000-0000-000000000000"), # no project file, nil UUID
    :Bobcat   => UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), # dummy UUID based on path
    :Cobra    => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), # UUID from project file
    :Dingo    => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), # UUID from project file
)
```

这是相应的图结构，以字典形式表示：

```julia
graph = Dict(
    # Bobcat:
    UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf") => Dict(
        :Cobra => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"),
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Cobra:
    UUID("4725e24d-f727-424b-bca0-c4307a3456fa") => Dict(
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Dingo:
    UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc") => Dict(),
)
```

一些需要注意的一般规则：

1. 一个没有项目文件的包可以依赖于任何顶级依赖项，并且由于包目录中的每个包都可以在顶层使用，因此它可以导入环境中的所有包。
2. 一个包含项目文件的包不能依赖于没有项目文件的包，因为包含项目文件的包只能加载 `graph` 中的包，而没有项目文件的包不会出现在 `graph` 中。
3. 一个包含项目文件但没有显式 UUID 的包只能被没有项目文件的包依赖，因为分配给这些包的虚拟 UUID 是严格内部的。

请观察以下这些规则在我们示例中的具体实例：

  * `土豚` 可以在 `美洲狮`、`眼镜蛇` 或 `丁哥` 上导入；它确实导入了 `美洲狮` 和 `眼镜蛇`。
  * `Bobcat` 可以并且确实导入 `Cobra` 和 `Dingo`，这两个都有 UUID 的项目文件，并在 `Bobcat` 的 `[deps]` 部分声明为依赖项。
  * `Bobcat` 不能依赖 `Aardvark`，因为 `Aardvark` 没有项目文件。
  * `Cobra` 可以并且确实导入 `Dingo`，后者有一个项目文件和 UUID，并在 `Cobra` 的 `[deps]` 部分声明为依赖项。
  * `Cobra` 不能依赖 `Aardvark` 或 `Bobcat`，因为它们都没有真实的 UUID。
  * `Dingo` 无法导入任何内容，因为它的项目文件没有 `[deps]` 部分。

**路径映射** 在包目录中是简单的：它将子目录名称映射到其对应的入口点路径。换句话说，如果我们示例项目目录的路径是 `/home/me/animals`，那么 `paths` 映射可以用这个字典表示：

```julia
paths = Dict(
    (UUID("00000000-0000-0000-0000-000000000000"), :Aardvark) =>
        "/home/me/AnimalPackages/Aardvark/src/Aardvark.jl",
    (UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), :Bobcat) =>
        "/home/me/AnimalPackages/Bobcat/src/Bobcat.jl",
    (UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), :Cobra) =>
        "/home/me/AnimalPackages/Cobra/src/Cobra.jl",
    (UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), :Dingo) =>
        "/home/me/AnimalPackages/Dingo/src/Dingo.jl",
)
```

由于包目录环境中的所有包根据定义都是具有预期入口文件的子目录，因此它们的 `paths` 映射条目总是具有这种形式。

### Environment stacks

第三种也是最后一种环境是通过叠加多个其他环境来组合其他环境，使每个环境中的包在一个单一的复合环境中可用。这些复合环境被称为 *环境堆栈*。Julia 的 `LOAD_PATH` 全局定义了一个环境堆栈——Julia 进程操作的环境。如果你希望你的 Julia 进程仅访问一个项目或包目录中的包，请将其设置为 `LOAD_PATH` 中的唯一条目。然而，能够访问一些你最喜欢的工具——标准库、分析器、调试器、个人工具等——通常是非常有用的，即使它们不是你正在处理的项目的依赖项。通过将包含这些工具的环境添加到加载路径中，你可以立即在顶层代码中访问它们，而无需将它们添加到你的项目中。

将环境栈组件的根、图形和路径数据结构合并的机制很简单：它们作为字典合并，在键冲突的情况下，优先考虑较早的条目。换句话说，如果我们有 `stack = [env₁, env₂, …]`，那么我们有：

```julia
roots = reduce(merge, reverse([roots₁, roots₂, …]))
graph = reduce(merge, reverse([graph₁, graph₂, …]))
paths = reduce(merge, reverse([paths₁, paths₂, …]))
```

下标的 `rootsᵢ`、`graphᵢ` 和 `pathsᵢ` 变量对应于 `stack` 中包含的下标环境 `envᵢ`。`reverse` 的存在是因为在其参数字典的键发生冲突时，`merge` 更倾向于最后一个参数而不是第一个参数。这个设计有几个值得注意的特点：

1. *主要环境*—即堆栈中的第一个环境—被忠实地嵌入到堆叠环境中。堆栈中第一个环境的完整依赖图保证完整地包含在堆叠环境中，包括所有依赖项的相同版本。
2. 非主环境中的包可能会使用不兼容版本的依赖项，即使它们自己的环境完全兼容。这种情况可能发生在它们的某个依赖项被堆栈中早期环境中的版本遮蔽时（无论是通过图形还是路径，或两者）。

由于主要环境通常是您正在进行的项目的环境，而堆栈后面的环境包含额外的工具，因此这是正确的权衡：破坏您的开发工具但保持项目正常工作更好。当发生这种不兼容时，您通常会希望将开发工具升级到与主项目兼容的版本。

### [Package Extensions](@id man-extensions)

一个“扩展”包是一个模块，当当前 Julia 会话中加载一组指定的其他包（其“触发器”）时，会自动加载该模块。扩展在项目文件的 `[extensions]` 部分定义。扩展的触发器是项目文件中 `[weakdeps]`（可能还有不常见的 `[deps]`）部分列出的那些包的子集。这些包可以像其他包一样具有兼容性条目。

```toml
name = "MyPackage"

[compat]
ExtDep = "1.0"
OtherExtDep = "1.0"

[weakdeps]
ExtDep = "c9a23..." # uuid
OtherExtDep = "862e..." # uuid

[extensions]
BarExt = ["ExtDep", "OtherExtDep"]
FooExt = "ExtDep"
...
```

`extensions` 下的键是扩展的名称。当右侧的所有包（该扩展的触发器）加载时，扩展会被加载。如果一个扩展只有一个触发器，触发器的列表可以简写为一个字符串。扩展的入口点位置要么在 `ext/FooExt.jl`，要么在 `ext/FooExt/FooExt.jl`，对于扩展 `FooExt`。扩展的内容通常结构如下：

```
module FooExt

# Load main package and triggers
using MyPackage, ExtDep

# Extend functionality in main package with types from the triggers
MyPackage.func(x::ExtDep.SomeStruct) = ...

end
```

当一个带有扩展的包被添加到环境中时，`weakdeps` 和 `extensions` 部分会存储在该包的清单文件中。包的依赖查找规则与其“父”包相同，唯一的区别是列出的触发器也被视为依赖项。

### [Package/Environment Preferences](@id preferences)

偏好设置是影响环境中包行为的元数据字典。偏好设置系统支持在编译时读取偏好设置，这意味着在加载代码时，我们必须确保Julia选择的预编译文件是使用与当前环境相同的偏好设置构建的，然后才能加载它们。用于修改偏好设置的公共API包含在[Preferences.jl](https://github.com/JuliaPackaging/Preferences.jl)包中。偏好设置作为TOML字典存储在当前活动项目旁边的`(Julia)LocalPreferences.toml`文件中。如果一个偏好设置被“导出”，它则存储在`(Julia)Project.toml`中。其目的是允许共享项目包含共享的偏好设置，同时允许用户自己在LocalPreferences.toml文件中覆盖这些偏好设置，该文件应如其名称所示被.gitignore。

在编译期间访问的偏好会自动标记为编译时偏好，任何对这些偏好的更改都会导致Julia编译器重新编译该模块的任何缓存预编译文件（`.ji`及相应的`.so`、`.dll`或`.dylib`文件）。这是通过在编译期间序列化所有编译时偏好的哈希值来完成的，然后在搜索要加载的适当文件时，将该哈希值与当前环境进行检查。

首选项可以通过仓库范围的默认值进行设置；如果在您的全局环境中安装了包 Foo 并且设置了首选项，这些首选项将适用，只要您的全局环境是 `LOAD_PATH` 的一部分。环境堆栈中更高层的首选项会被加载路径中更接近的条目覆盖，最终以当前活动项目结束。这允许存在仓库范围的首选项默认值，活动项目能够合并或甚至完全覆盖这些继承的首选项。有关如何设置首选项以允许或禁止合并的完整细节，请参见 `Preferences.set_preferences!()` 的文档字符串。

## Conclusion

联邦包管理和精确的软件可重现性在包系统中是困难但值得追求的目标。结合这两个目标，导致的包加载机制比大多数动态语言更复杂，但它也带来了更常与静态语言相关的可扩展性和可重现性。通常，Julia 用户应该能够使用内置的包管理器来管理他们的项目，而无需对这些交互有精确的理解。调用 `Pkg.add("X")` 将添加到通过 `Pkg.activate("Y")` 选择的适当项目和清单文件中，以便将来调用 `import X` 时可以无须进一步思考地加载 `X`。
