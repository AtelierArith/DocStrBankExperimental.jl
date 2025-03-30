# `EscapeAnalysis`

`Core.Compiler.EscapeAnalysis` 是一个编译器实用模块，旨在分析 [Julia's SSA-form IR](@ref Julia-SSA-form-IR) 也就是 `IRCode` 的逃逸信息。

此逃逸分析旨在：

  * 利用Julia的高级语义，特别是通过跨过程调用来推理逃逸和别名。
  * 足够灵活，可以用于各种优化，包括 [alias-aware SROA](https://github.com/JuliaLang/julia/pull/43888)、[early `finalize` insertion](https://github.com/JuliaLang/julia/pull/44056)、[copy-free `ImmutableArray` construction](https://github.com/JuliaLang/julia/pull/42465)、可变对象的栈分配等。
  * 实现一个基于完全反向数据流分析实现的简单实现，以及一个结合正交格属性的新格设计。

## Try it out!

您可以尝试逃逸分析，通过加载 `EAUtils.jl` 实用脚本，该脚本定义了方便的条目 `code_escapes` 和 `@code_escapes` 以用于测试和调试目的：

```@repl EAUtils
let JULIA_DIR = normpath(Sys.BINDIR, "..", "share", "julia")
    # load `EscapeAnalysis` module to define the core analysis code
    include(normpath(JULIA_DIR, "base", "compiler", "ssair", "EscapeAnalysis", "EscapeAnalysis.jl"))
    using .EscapeAnalysis
    # load `EAUtils` module to define the utilities
    include(normpath(JULIA_DIR, "test", "compiler", "EscapeAnalysis", "EAUtils.jl"))
    using .EAUtils
end

mutable struct SafeRef{T}
    x::T
end
Base.getindex(x::SafeRef) = x.x;
Base.setindex!(x::SafeRef, v) = x.x = v;
Base.isassigned(x::SafeRef) = true;
get′(x) = isassigned(x) ? x[] : throw(x);

result = code_escapes((String,String,String,String)) do s1, s2, s3, s4
    r1 = Ref(s1)
    r2 = Ref(s2)
    r3 = SafeRef(s3)
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    s3 = get′(r3)       # still `r3` doesn't escape fully
    s4 = sizeof(s4)     # the argument `s4` doesn't escape here
    return s2, s3, s4
end
```

每个调用参数和SSA语句旁边的符号表示以下含义：

  * `◌`（普通）：此值未被分析，因为它的转义信息无论如何都不会被使用（例如，当对象是`isbitstype`时）
  * `✓`（绿色或青色）：此值永远不会逃逸（`has_no_escape(result.state[x])` 为真），如果它也有参数逃逸，则为蓝色（`has_arg_escape(result.state[x])` 为真）
  * `↑`（蓝色或黄色）：此值可以通过返回逃逸到调用者（`has_return_escape(result.state[x])` 为真），如果它还有未处理的抛出逃逸（`has_thrown_escape(result.state[x])` 为真），则标记为黄色。
  * `X`（红色）：这个值可以逃逸到逃逸分析无法推理的地方，比如逃逸到全局内存（`has_all_escape(result.state[x])` 为真）
  * `*` (bold): this value's escape state is between the `ReturnEscape` and `AllEscape` in the partial order of [`EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo), colored yellow if it has unhandled thrown escape also (`has_thrown_escape(result.state[x])` holds)
  * `′`: 此值在其 `AliasInfo` 属性中具有额外的对象字段/数组元素信息

每个调用参数和SSA值的逃逸信息可以像下面这样以编程方式进行检查：

```@repl EAUtils
result.state[Core.Argument(3)] # get EscapeInfo of `s2`

result.state[Core.SSAValue(3)] # get EscapeInfo of `r3`
```

## Analysis Design

### Lattice Design

`EscapeAnalysis` 被实现为一个 [data-flow analysis](https://en.wikipedia.org/wiki/Data-flow_analysis)，它在一个 [`x::EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo) 的格上工作，该格由以下属性组成：

  * `x.Analyzed::Bool`：并不是格的正式组成部分，仅表示 `x` 尚未被分析或未分析。
  * `x.ReturnEscape::BitSet`: 记录 SSA 语句，其中 `x` 可以通过返回逃逸到调用者
  * `x.ThrownEscape::BitSet`: 记录可以作为异常抛出的 SSA 语句（用于下面描述的 [exception handling](@ref EA-Exception-Handling)）
  * `x.AliasInfo`：维护所有可能的值，这些值可以被别名为 `x` 的字段或数组元素（用于下面描述的 [alias analysis](@ref EA-Alias-Analysis)）
  * `x.ArgEscape::Int`（尚未实现）：表示它将通过对参数使用 `setfield!` 来逃逸到调用者。

这些属性可以组合在一起创建一个具有有限高度的部分格，前提是输入程序的语句数量是有限的，这一点由Julia的语义保证。这个格设计的巧妙之处在于，它通过允许每个格属性单独处理，从而简化了格操作的实现[^LatticeDesign]。

### Backward Escape Propagation

此逃逸分析实现基于论文中描述的数据流算法[^MM02]。该分析在`EscapeInfo`的格上工作，并将格元素从底部过渡到顶部，直到每个格元素收敛到一个固定点，通过维护一个（概念上的）工作集，该工作集包含与待分析的剩余SSA语句对应的程序计数器。该分析管理一个单一的全局状态，跟踪每个参数和SSA语句的`EscapeInfo`，但还要注意，一些流敏感性被编码为记录在`EscapeInfo`的`ReturnEscape`属性中的程序计数器，这可以在必要时与支配分析结合使用，以推理流敏感性。

这种逃逸分析的一个独特设计是它完全是*向后*的，即逃逸信息从*使用*流向*定义*。例如，在下面的代码片段中，EA首先分析语句`return %1`并对`%1`（对应于`obj`）施加`ReturnEscape`，然后它分析`%1 = %new(Base.RefValue{String, _2}))`并将施加在`%1`上的`ReturnEscape`传播到调用参数`_2`（对应于`s`）：

```@repl EAUtils
code_escapes((String,)) do s
    obj = Ref(s)
    return obj
end
```

关键观察在于，这种反向分析允许逃逸信息沿着使用-定义链自然流动，而不是控制流[^BackandForth]。因此，这种方案使得逃逸分析的简单实现成为可能，例如，`PhiNode` 可以通过将施加在 `PhiNode` 上的逃逸信息传播到其前驱值来简单处理：

```@repl EAUtils
code_escapes((Bool, String, String)) do cnd, s, t
    if cnd
        obj = Ref(s)
    else
        obj = Ref(t)
    end
    return obj
end
```

### [Alias Analysis](@id EA-Alias-Analysis)

`EscapeAnalysis` 实现了一种向后字段分析，以便以某种准确性推理对象字段上施加的逃逸情况，而 `x::EscapeInfo` 的 `x.AliasInfo` 属性正是为此目的而存在。它记录了在“使用”位置可能与 `x` 的字段别名的所有可能值，然后这些记录值的逃逸信息在“定义”位置传播到实际字段值。更具体地说，该分析通过分析 `getfield` 调用记录一个可能与对象字段别名的值，然后在分析 `%new(...)` 表达式或 `setfield!` 调用时将其逃逸信息传播到字段[^Dynamism]。

```@repl EAUtils
code_escapes((String,)) do s
    obj = SafeRef("init")
    obj[] = s
    v = obj[]
    return v
end
```

在上面的例子中，施加在 `%3`（对应于 `v`）上的 `ReturnEscape` *并没有* 直接传播到 `%1`（对应于 `obj`），而是 `ReturnEscape` 仅传播到 `_2`（对应于 `s`）。在这里，`%3` 被记录在 `%1` 的 `AliasInfo` 属性中，因为它可以与 `%1` 的第一个字段别名，然后在分析 `Base.setfield!(%1, :x, _2)::String` 时，该逃逸信息被传播到 `_2`，但没有传播到 `%1`。

所以 `EscapeAnalysis` 跟踪哪些 IR 元素可以在 `getfield`-`%new`/`setfield!` 链中被别名化，以分析对象字段的逃逸，但实际上这种别名分析需要被推广以处理其他 IR 元素。这是因为在 Julia IR 中，同一个对象有时会由不同的 IR 元素表示，因此我们应该确保那些实际上可以表示同一个对象的不同 IR 元素共享相同的逃逸信息。返回相同对象作为其操作数的 IR 元素，例如 `PiNode` 和 `typeassert`，可能会导致 IR 级别的别名化，因此需要对任何此类别名值施加的逃逸信息在它们之间共享。更有趣的是，这对于正确推理 `PhiNode` 上的变异也是必要的。让我们考虑以下示例：

```@repl EAUtils
code_escapes((Bool, String,)) do cond, x
    if cond
        ϕ2 = ϕ1 = SafeRef("foo")
    else
        ϕ2 = ϕ1 = SafeRef("bar")
    end
    ϕ2[] = x
    y = ϕ1[]
    return y
end
```

`ϕ1 = %5` 和 `ϕ2 = %6` 是别名，因此对 `%8 = Base.getfield(%6, :x)::String`（对应于 `y = ϕ1[]`）施加的 `ReturnEscape` 需要传播到 `Base.setfield!(%5, :x, _3)::String`（对应于 `ϕ2[] = x`）。为了正确传播这种逃逸信息，分析应该识别出 `ϕ1` 和 `ϕ2` 的 *前驱* 也可能是别名，并使它们的逃逸信息相等。

这种别名信息的一个有趣特性是，它在“使用”位置是未知的，但只能在“定义”位置推导出来（因为别名在概念上等同于赋值），因此它并不自然适合向后分析。为了有效地在相关值之间传播逃逸信息，EscapeAnalysis.jl 使用了一种受旧JVM论文中解释的逃逸分析算法启发的方法[^JVM05]。也就是说，除了管理逃逸格子元素外，分析还维护一个“等价”别名集，这是一个不相交的别名参数和SSA语句的集合。别名集管理可以相互别名的值，并允许对任何这样的别名值施加的逃逸信息在它们之间进行等化。

### [Array Analysis](@id EA-Array-Analysis)

上述描述的对象字段的别名分析也可以推广到分析数组操作。`EscapeAnalysis` 实现了对各种原始数组操作的处理，以便通过 `arrayref`-`arrayset` 使用-定义链传播逃逸，并且不会过于保守地逃逸已分配的数组：

```@repl EAUtils
code_escapes((String,)) do s
    ary = Any[]
    push!(ary, SafeRef(s))
    return ary[1], length(ary)
end
```

在上述示例中，`EscapeAnalysis` 理解 `%20` 和 `%2`（对应于分配的对象 `SafeRef(s)`）通过 `arrayset`-`arrayref` 链相互别名，并对它们施加 `ReturnEscape`，但不对分配的数组 `%1`（对应于 `ary`）施加此限制。`EscapeAnalysis` 仍然对 `ary` 施加 `ThrownEscape`，因为它还需要考虑通过 `BoundsError` 可能发生的逃逸，但也要注意，这种未处理的 `ThrownEscape` 在优化 `ary` 分配时通常可以被忽略。

此外，在能够*精确*知道数组索引信息以及数组维度的情况下，`EscapeAnalysis` 甚至能够通过 `arrayref`-`arrayset` 链推理关于“每个元素”的别名，因为 `EscapeAnalysis` 对对象进行“每个字段”的别名分析：

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Vector{Any}(undef, 2)
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

注意，`ReturnEscape` 仅对 `%2`（对应于 `SafeRef(s)`）施加，但不对 `%4`（对应于 `SafeRef(t)`）施加。这是因为分配的数组的维度和与所有 `arrayref`/`arrayset` 操作相关的索引作为常量信息可用，并且 `EscapeAnalysis` 可以理解 `%6` 与 `%2` 是别名，但永远不会与 `%4` 是别名。在这种情况下，后续的优化过程将能够用 `%2` 替换 `Base.arrayref(true, %1, 1)::Any`（即“加载转发”），并最终完全消除数组 `%1` 的分配（即“标量替换”）。

与对象字段分析相比，对象字段的访问可以通过推断得出的类型信息轻松分析，而数组维度并未作为类型信息编码，因此我们需要额外的分析来推导该信息。此时的 `EscapeAnalysis` 首先进行额外的简单线性扫描，以分析分配数组的维度，然后再启动主要分析例程，以便后续的逃逸分析能够准确分析对这些数组的操作。

然而，这种精确的“逐元素”别名分析往往很困难。基本上，数组固有的主要困难在于数组的维度和索引通常是非常量的：

  * 循环经常产生循环变体，非恒定数组索引
  * （特定于向量）数组调整大小会改变数组维度并使其常量性失效

让我们通过具体例子来讨论这些困难。

在以下示例中，`EscapeAnalysis` 由于 `Base.arrayset(false, %4, %8, %6)::Vector{Any}` 中的索引不是（简单地）常量，因此未能进行精确的别名分析。特别是 `Any[nothing, nothing]` 形成一个循环，并在循环中调用该 `arrayset` 操作，其中 `%6` 被表示为一个 ϕ 节点值（其值依赖于控制流）。因此，`ReturnEscape` 最终被施加在 `%23`（对应于 `SafeRef(s)`）和 `%25`（对应于 `SafeRef(t)`）上，尽管理想情况下我们希望它仅施加在 `%23` 上，而不施加在 `%25` 上：

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[nothing, nothing]
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

以下示例说明了向量调整大小如何使精确别名分析变得困难。根本的困难在于分配的数组 `%1` 的维度最初被初始化为 `0`，但在之后的两个 `:jl_array_grow_end` 调用中发生了变化。`EscapeAnalysis` 目前在遇到任何数组调整大小操作时简单地放弃精确别名分析，因此对 `%2`（对应于 `SafeRef(s)`）和 `%20`（对应于 `SafeRef(t)`）施加了 `ReturnEscape`。

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[]
    push!(ary, SafeRef(s))
    push!(ary, SafeRef(t))
    ary[1], length(ary)
end
```

为了应对这些困难，我们需要推理能够意识到数组维度，并以流敏感的方式传播数组维度[^ArrayDimension]，同时提出循环变值的良好表示。

`EscapeAnalysis` 此时迅速切换到更不精确的分析，在数组维度或索引显然非常非常量的情况下，不跟踪精确的索引信息。这个切换可以自然地实现为数据流分析框架中 `EscapeInfo.AliasInfo` 属性的格连接操作。

### [Exception Handling](@id EA-Exception-Handling)

值得注意的是，`EscapeAnalysis` 如何处理通过异常可能发生的逃逸。表面上看，将施加在 `:the_exception` 对象上的逃逸信息传播到可能在相应的 `try` 块中抛出的所有值似乎就足够了。但实际上，在 Julia 中还有几种其他方式可以访问异常对象，例如 `Base.current_exceptions` 和 `rethrow`。例如，逃逸分析需要考虑下面示例中 `r` 的潜在逃逸：

```@repl EAUtils
const GR = Ref{Any}();
@noinline function rethrow_escape!()
    try
        rethrow()
    catch err
        GR[] = err
    end
end;
get′(x) = isassigned(x) ? x[] : throw(x);

code_escapes() do
    r = Ref{String}()
    local t
    try
        t = get′(r)
    catch err
        t = typeof(err)   # `err` (which `r` aliases to) doesn't escape here
        rethrow_escape!() # but `r` escapes here
    end
    return t
end
```

它需要进行全球分析，以便正确推理通过现有异常接口的所有可能逃逸。目前，我们总是保守地将最上层的逃逸信息传播到所有可能抛出的对象，因为考虑到异常处理和错误路径通常不需要非常敏感的性能，这样的额外分析可能不值得进行，并且错误路径的优化可能无效，因为它们通常出于延迟原因故意“未优化”。

`x::EscapeInfo` 的 `x.ThrownEscape` 属性记录了可以作为异常抛出的 SSA 语句。利用这些信息，`EscapeAnalysis` 可以有限地传播可能的通过异常逃逸，仅限于每个 `try` 区域中可能抛出的内容：

```@repl EAUtils
result = code_escapes((String,String)) do s1, s2
    r1 = Ref(s1)
    r2 = Ref(s2)
    local ret
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    return s2
end
```

## Analysis Usage

`analyze_escapes` 是分析 SSA-IR 元素逃逸信息的入口点。

大多数优化，如 SROA (`sroa_pass!`)，在应用于经过优化的源代码时更有效，这些源代码通过内联传递 (`ssa_inlining_pass!`) 解决了跨过程调用并扩展了被调用者源。相应地，`analyze_escapes` 也能够分析内联后的 IR，并收集对某些与内存相关的优化有用的逃逸信息。

然而，由于某些优化过程，如内联，可能会改变控制流并消除无效代码，因此它们可能会破坏逃逸信息的跨过程有效性。特别是，为了收集跨过程有效的逃逸信息，我们需要分析一个预内联的中间表示（IR）。

由于这个原因，`analyze_escapes` 可以在任何 Julia 级别的优化阶段分析 `IRCode`，特别是，它应该在以下两个阶段使用：

  * `IPO EA`: 分析预内联 IR 以生成 IPO 有效的逃逸信息缓存
  * `Local EA`: 分析后内联的中间表示以收集局部有效的逃逸信息

逃逸信息由 `IPO EA` 转换为 `ArgEscapeCache` 数据结构并全局缓存。通过将适当的 `get_escape_cache` 回调传递给 `analyze_escapes`，逃逸分析可以通过利用之前 `IPO EA` 导出的非内联被调用者的缓存跨过程信息来提高分析准确性。更有趣的是，使用 `IPO EA` 逃逸信息进行类型推断也是有效的，例如，通过形成可变对象的 `Const`/`PartialStruct`/`MustAlias` 可以提高推断准确性。

```@docs
Core.Compiler.EscapeAnalysis.analyze_escapes
Core.Compiler.EscapeAnalysis.EscapeState
Core.Compiler.EscapeAnalysis.EscapeInfo
```

---

[^LatticeDesign]: Our type inference implementation takes the alternative approach, where each lattice property is represented by a special lattice element type object. It turns out that it started to complicate implementations of the lattice operations mainly because it often requires conversion rules between each lattice element type object. And we are working on [overhauling our type inference lattice implementation](https://github.com/JuliaLang/julia/pull/42596) with `EscapeInfo`-like lattice design.

[^MM02]: *A Graph-Free approach to Data-Flow Analysis*.      Markas Mohnen, 2002, April.      [https://api.semanticscholar.org/CorpusID:28519618](https://api.semanticscholar.org/CorpusID:28519618).

[^BackandForth]: Our type inference algorithm in contrast is implemented as a forward analysis, because type information usually flows from "definition" to "usage" and it is more natural and effective to propagate such information in a forward way.

[^Dynamism]: In some cases, however, object fields can't be analyzed precisely. For example, object may escape to somewhere `EscapeAnalysis` can't account for possible memory effects on it, or fields of the objects simply can't be known because of the lack of type information. In such cases `AliasInfo` property is raised to the topmost element within its own lattice order, and it causes succeeding field analysis to be conservative and escape information imposed on fields of an unanalyzable object to be propagated to the object itself.

[^JVM05]: *Escape Analysis in the Context of Dynamic Compilation and Deoptimization*.       Thomas Kotzmann and Hanspeter Mössenböck, 2005, June.       [https://dl.acm.org/doi/10.1145/1064979.1064996](https://dl.acm.org/doi/10.1145/1064979.1064996).

[^ArrayDimension]: Otherwise we will need yet another forward data-flow analysis on top of the escape analysis.
