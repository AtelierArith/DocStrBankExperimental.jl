# Julia SSA-form IR

Julia 使用静态单赋值中间表示 ([SSA IR](https://en.wikipedia.org/wiki/Static_single-assignment_form)) 来执行优化。这个 IR 与 LLVM IR 不同，并且是 Julia 特有的。它允许进行 Julia 特定的优化。

1. 基本块（没有控制流的区域）被明确标注。
2. 如果/否则和循环被转换为 `goto` 语句。
3. 通过引入变量，将包含多个操作的行拆分为多行。

例如以下的 Julia 代码：

```julia
function foo(x)
    y = sin(x)
    if x > 5.0
        y = y + cos(x)
    end
    return exp(2) + y
end
```

当使用 `Float64` 参数调用时，翻译为：

```julia
using InteractiveUtils
@code_typed foo(1.0)
```

```llvm
CodeInfo(
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
2 ─ %4 = invoke Main.cos(x::Float64)::Float64
└── %5 = Base.add_float(%1, %4)::Float64
3 ┄ %6 = φ (#2 => %5, #1 => %1)::Float64
│   %7 = Base.add_float(7.38905609893065, %6)::Float64
└──      return %7
) => Float64
```

在这个例子中，我们可以看到所有这些变化。

1. 第一个基本块是所有内容在

```llvm
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
```

2. `if` 语句被翻译为 `goto #3 if not %2`，如果不满足 `x>5`，则跳转到第三个基本块，否则跳转到第二个基本块。
3. `%2` 是一个引入的 SSA 值，用于表示 `x > 5`。

## Background

从 Julia 0.7 开始，编译器的部分使用了一种新的 [SSA-form](https://en.wikipedia.org/wiki/Static_single_assignment_form) 中间表示 (IR)。历史上，编译器会直接从降低形式的 Julia AST 生成 LLVM IR。这种形式去除了大部分语法抽象，但仍然看起来像一个抽象语法树。随着时间的推移，为了促进优化，SSA 值被引入到这个 IR 中，并且 IR 被线性化（即转变为一种形式，其中函数参数只能是 SSA 值或常量）。然而，由于 IR 中缺乏 Phi 节点（这是处理反向边和条件控制流重新合并所必需的），非 SSA 值（槽）仍然存在于 IR 中。这在进行中间端优化时 negated 了 SSA 形式表示的许多有用性。为了使这些优化在没有完整 SSA 形式表示的情况下工作，付出了巨大的努力，但缺乏这种表示最终证明是不可行的。

## Categories of IR nodes

SSA IR 表示有四类 IR 节点：Phi、Pi、PhiC 和 Upsilon 节点（后两者仅用于异常处理）。

### Phi nodes and Pi nodes

Phi 节点是通用 SSA 抽象的一部分（如果您不熟悉这个概念，请参见上面的链接）。在 Julia IR 中，这些节点表示为：

```
struct PhiNode
    edges::Vector{Int32}
    values::Vector{Any}
end
```

在这里，我们确保两个向量始终具有相同的长度。在规范表示中（由代码生成器和解释器处理的表示），边值指示来源语句编号（即，如果边的条目为 `15`，则必须有一个 `goto`、`gotoifnot` 或从语句 `15` 隐式落入的语句，目标是这个 phi 节点）。值可以是 SSA 值或常量。如果变量在此路径上未定义，则值也可以是未分配的。然而，未定义性检查会在中间端优化后显式插入并表示为布尔值，因此代码生成器可以假设对 Phi 节点的任何使用在相应的槽中都有一个分配的值。映射不完整也是合法的，即一个 Phi 节点可以缺少传入边。在这种情况下，必须动态保证相应的值不会被使用。

请注意，SSA 在相应前驱的终止符之后语义上发生（“在边缘上”）。因此，如果多个 Phi 节点出现在基本块的开头，它们会同时运行。这意味着在以下 IR 代码片段中，如果我们来自块 `23`，那么 `%46` 将在我们进入该块之前获取与 `%45` 相关联的值。

```julia
%45 = φ (#18 => %23, #23 => %50)
%46 = φ (#18 => 1.0, #23 => %45)
```

PiNodes 编码了静态证明的信息，这些信息可能在由给定 pi 节点主导的基本块中隐式假定。它们在概念上等同于论文中介绍的技术 [ABCD: Eliminating Array Bounds Checks on Demand](https://dl.acm.org/citation.cfm?id=358438.349342) 或 LLVM 中的谓词信息节点。要了解它们是如何工作的，可以考虑，例如。

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    # use x
else
    # use x
end
```

我们可以执行谓词插入并将其转化为：

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    %x_int = PiNode(x, Int)
    # use %x_int
else
    %x_float = PiNode(x, Float64)
    # use %x_float
end
```

Pi 节点在解释器中通常被忽略，因为它们对值没有任何影响，但有时可能会导致编译器中的代码生成（例如，从隐式联合分裂表示更改为普通的未包装表示）。Pi 节点的主要用处在于，值的路径条件可以通过 def-use 链遍历简单地累积，这通常是针对这些条件而进行的大多数优化所做的。

### PhiC nodes and Upsilon nodes

异常处理在一定程度上使SSA的故事变得复杂，因为异常处理在IR中引入了额外的控制流边缘，必须跟踪这些边缘上的值。LLVM采用的一种方法是将可能抛出异常的调用放入基本块终结器，并向捕获处理程序添加一个显式的控制流边缘：

```
invoke @function_that_may_throw() to label %regular unwind to %catch

regular:
# Control flow continues here

catch:
# Exceptions go here
```

然而，在像 Julia 这样的语言中，这会造成问题，因为在优化管道的开始，我们不知道哪些调用会抛出异常。我们必须保守地假设每个调用（在 Julia 中是每个语句）都会抛出异常。这将产生几个负面影响。一方面，这将基本上将每个基本块的范围缩小到单个调用，违背了在基本块级别执行操作的目的。另一方面，每个捕获基本块将具有 `n*m` 个 phi 节点参数（`n` 是关键区域中的语句数量，`m` 是通过捕获块的活值数量）。

为了绕过这个问题，我们使用 `Upsilon` 和 `PhiC` 节点的组合（C 代表 `catch`，在 IR 美化打印中写作 `φᶜ`，因为 unicode 下标 c 不可用）。可以有几种方式来理解这些节点，但也许最简单的方式是将每个 `PhiC` 视为从一个唯一的存储-多次、读取-一次的槽中加载，而 `Upsilon` 则是相应的存储操作。`PhiC` 拥有一个操作数列表，包含所有存储到其隐式槽的 upsilon 节点。然而，`Upsilon` 节点并不记录它们存储到哪个 `PhiC` 节点。这是为了与其余的 SSA IR 更自然地集成。例如，如果没有更多对 `PhiC` 节点的使用，则可以安全地删除它，`Upsilon` 节点也是如此。在大多数 IR 传递中，`PhiC` 节点可以像 `Phi` 节点一样处理。可以通过它们跟踪使用-定义链，并且可以将它们提升到新的 `PhiC` 节点和新的 `Upsilon` 节点（在与原始 `Upsilon` 节点相同的位置）。这个方案的结果是，`Upsilon` 节点（和 `PhiC` 参数）的数量与特定变量的赋值数量成正比（在 SSA 转换之前），而不是与关键区域中的语句数量成正比。

要查看此方案的实际应用，请考虑该函数

```julia
@noinline opaque() = invokelatest(identity, nothing) # Something opaque
function foo()
    local y
    x = 1
    try
        y = 2
        opaque()
        y = 3
        error()
    catch
    end
    (x, y)
end
```

相应的 IR（去除无关类型后）是：

```
1 ─       nothing::Nothing
2 ─ %2  = $(Expr(:enter, #4))
3 ─ %3  = ϒ (false)
│   %4  = ϒ (#undef)
│   %5  = ϒ (1)
│   %6  = ϒ (true)
│   %7  = ϒ (2)
│         invoke Main.opaque()::Any
│   %9  = ϒ (true)
│   %10 = ϒ (3)
│         invoke Main.error()::Union{}
└──       $(Expr(:unreachable))::Union{}
4 ┄ %13 = φᶜ (%3, %6, %9)::Bool
│   %14 = φᶜ (%4, %7, %10)::Core.Compiler.MaybeUndef(Int64)
│   %15 = φᶜ (%5)::Core.Const(1)
└──       $(Expr(:leave, Core.SSAValue(2)))
5 ─       $(Expr(:pop_exception, :(%2)))::Any
│         $(Expr(:throw_undef_if_not, :y, :(%13)))::Any
│   %19 = Core.tuple(%15, %14)
└──       return %19
```

特别注意，每个值在临界区域内都会在临界区域的顶部获得一个 upsilon 节点。这是因为 catch 块被认为具有来自函数外部的不可见控制流边缘。因此，没有 SSA 值主导 catch 块，所有传入值必须通过 `φᶜ` 节点。

## Main SSA data structure

主要的 `SSAIR` 数据结构值得讨论。它受到 LLVM 和 Webkit 的 B3 IR 的启发。数据结构的核心是一个平坦的语句向量。每个语句根据其在向量中的位置隐式地分配一个 SSA 值（即，索引为 1 的语句的结果可以使用 `SSAValue(1)` 访问等）。对于每个 SSA 值，我们还维护其类型。由于 SSA 值在定义上只被分配一次，因此该类型也是对应索引处表达式的结果类型。然而，尽管这种表示相当高效（因为分配不需要显式编码），但它当然带来了一个缺点，即顺序在语义上是重要的，因此重新排序和插入会改变语句编号。此外，我们不保留使用列表（即，从定义到所有使用的遍历是不可能的，除非显式计算此映射——然而，定义列表是微不足道的，因为您可以从索引查找相应的语句），因此 LLVM 风格的 RAUW（替换所有使用）操作不可用。

相反，我们做以下事情：

  * 我们保持一个单独的节点缓冲区以进行插入（包括插入位置、相应值的类型和节点本身）。这些节点按其在插入缓冲区中的出现顺序编号，从而允许它们的值可以立即在 IR 的其他地方使用（即，如果原始语句列表中有 12 个语句，第一个新语句将可以作为 `SSAValue(13)` 访问）。
  * RAUW 风格的操作是通过将相应的语句索引设置为替换值来执行的。
  * 语句通过将相应的语句设置为 `nothing` 来被删除（这本质上只是上述内容的一种特殊情况约定）。
  * 如果有任何使用该语句的地方被删除，它们将被设置为 `nothing`。

有一个 `compact!` 函数，它通过在适当的位置插入节点、进行微不足道的复制传播以及将使用重命名为任何更改的 SSA 值来压缩上述数据结构。然而，这个方案的巧妙之处在于，这种压缩可以作为后续遍历的一部分懒惰地完成。大多数优化遍历需要遍历整个语句列表，在此过程中进行分析或修改。我们提供了一个 `IncrementalCompact` 迭代器，可以用来遍历语句列表。它将执行任何必要的压缩，并返回节点的新索引以及节点本身。在这一点上，遍历定义-使用链是合法的，并且可以对 IR 进行任何修改或删除（但是不允许插入）。

这种安排的想法是，由于优化过程需要访问相应的内存并承担相应的内存访问开销，因此执行额外的管理工作应该相对开销较小（并且可以节省在中间表示修改期间维护这些数据结构的开销）。
