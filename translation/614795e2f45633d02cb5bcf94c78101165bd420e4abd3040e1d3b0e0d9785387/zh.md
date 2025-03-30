# [Documentation](@id man-documentation)

## Accessing Documentation

文档可以在 REPL 或通过输入 `?` 后跟函数或宏的名称，然后按 `Enter` 访问，网址为 [IJulia](https://github.com/JuliaLang/IJulia.jl)。例如，

```julia
?cos
?@time
?r""
```

将分别显示相关函数、宏或字符串宏的文档。大多数Julia环境提供了一种直接访问文档的方法：

  * [VS Code](https://www.julia-vscode.org/) 在你悬停在函数名称上时显示文档。你也可以使用侧边栏中的 Julia 面板来搜索文档。
  * 在 [Pluto](https://github.com/fonsp/Pluto.jl) 中，打开右下角的“实时文档”面板。
  * 在 [Juno](https://junolab.org) 中使用 `Ctrl-J, Ctrl-D` 将显示光标下对象的文档。

`Docs.hasdoc(module, name)::Bool` 告诉我们一个名称是否有文档字符串。 `Docs.undocumented_names(module; all)` 返回模块中的未文档化名称。

## Writing Documentation

Julia 使得包开发者和用户能够通过内置文档系统轻松地为函数、类型和其他对象编写文档。

基本语法很简单：出现在对象（函数、宏、类型或实例）之前的任何字符串将被解释为对其的文档说明（这些称为 *docstrings*）。请注意，文档字符串与被文档化对象之间不得有空行或注释。以下是一个基本示例：

```julia
"Tell whether there are too foo items in the array."
foo(xs::Array) = ...
```

文档被解释为 [Markdown](https://en.wikipedia.org/wiki/Markdown)，因此您可以使用缩进和代码围栏将代码示例与文本分隔开。从技术上讲，任何对象都可以与任何其他对象关联作为元数据；Markdown 恰好是默认值，但也可以构造其他字符串宏并将它们传递给 `@doc` 宏。

!!! note
    Markdown 支持已在 `Markdown` 标准库中实现，完整的支持语法列表请参见 [documentation](@ref markdown_stdlib)。


这里是一个更复杂的例子，仍然使用Markdown：

````julia
"""
    bar(x[, y])

Compute the Bar index between `x` and `y`.

If `y` is unspecified, compute the Bar index between all pairs of columns of `x`.

# Examples
```julia-repl
julia> bar([1, 2], [1, 2])
1
```
"""
function bar(x, y) ...
````

如上例所示，我们建议在编写文档时遵循一些简单的惯例：

1. 始终在文档顶部显示函数的签名，使用四个空格缩进，以便将其作为Julia代码打印。

    这可以与Julia代码中存在的签名相同（如`mean(x::AbstractArray)`），或简化形式。可选参数应尽可能用其默认值表示（即`f(x, y=1)`），遵循实际的Julia语法。没有默认值的可选参数应放在括号中（即`f(x[, y])`和`f(x[, y[, z]])`）。另一种解决方案是使用多行：一行没有可选参数，其他行带有可选参数。此解决方案也可用于记录给定函数的多个相关方法。当一个函数接受多个关键字参数时，仅在签名中包含`<keyword arguments>`占位符（即`f(x; <keyword arguments>)`），并在`# Arguments`部分给出完整列表（见下面第4点）。
2. 在简化的签名块后包含一行描述该函数的作用或该对象所代表的内容。如果需要，在空行后提供更多细节。

    使用命令式形式编写单行句子（“执行此操作”，“返回该值”），而不是第三人称（不要写“返回长度...”）来记录函数。句子应以句号结束。如果函数的含义无法轻松总结，将其拆分为可组合的独立部分可能是有益的（不过这不应被视为对每个单独情况的绝对要求）。
3. 请不要重复自己。

    由于函数名称由签名给出，因此无需以“函数 `bar`...”开头文档：直接切入主题。同样，如果签名指定了参数的类型，在描述中提及它们是多余的。
4. 仅在真正必要时提供参数列表。

    对于简单函数，直接在函数目的的描述中提及参数的角色通常更清晰。参数列表只会重复其他地方已经提供的信息。然而，对于具有多个参数（特别是关键字参数）的复杂函数，提供参数列表可能是个好主意。在这种情况下，将其插入到函数的一般描述之后，在 `# Arguments` 标题下，每个参数用一个 `-` 项列出。列表应提及参数的类型和默认值（如果有的话）：

    ```julia
    """
    ...
    # Arguments
    - `n::Integer`: the number of elements to compute.
    - `dim::Integer=1`: the dimensions along which to perform the computation.
    ...
    """
    ```
5. 提供相关函数的提示。

    有时会有相关功能的函数。为了提高可发现性，请在 `另请参阅` 段落中提供这些函数的简短列表。

    ```
    See also [`bar!`](@ref), [`baz`](@ref), [`baaz`](@ref).
    ```
6. Include any code examples in an `# Examples` section.

    示例应尽可能以 *doctests* 的形式编写。*doctest* 是一个围栏代码块（参见 [Code blocks](@ref)），以 ````` ```jldoctest````` 开头，并包含任意数量的 `julia>` 提示符以及输入和预期输出，这些都模仿 Julia REPL。

    !!! note
        Doctests 通过 [`Documenter.jl`](https://github.com/JuliaDocs/Documenter.jl) 启用。有关更详细的文档，请参见 Documenter's [manual](https://juliadocs.github.io/Documenter.jl/)。


    例如在以下文档字符串中，定义了一个变量 `a`，并且预期结果，如在 Julia REPL 中打印的，随后出现：

    ````julia
    """
    Some nice documentation here.

    # Examples
    ```jldoctest
    julia> a = [1 2; 3 4]
    2×2 Array{Int64,2}:
     1  2
     3  4
    ```
    """
    ````

    !!! warning
        在 doctests 中应避免调用 `rand` 和其他与随机数生成器相关的函数，因为它们在不同的 Julia 会话中不会产生一致的输出。如果您想展示一些与随机数生成相关的功能，一个选项是显式构造并初始化您自己的 RNG 对象（参见 [`Random`](@ref Random-Numbers)），并将其传递给您正在进行 doctest 的函数。

        操作系统字大小（[`Int32`](@ref) 或 [`Int64`](@ref)）以及路径分隔符的差异（`/` 或 `\`）也会影响某些文档测试的可重复性。

        请注意，您在 doctest 中的空格是重要的！如果您错误地对齐了数组的美观打印输出，doctest 将会失败。


    您可以运行 `make -C doc doctest=true` 来运行 Julia 手册和 API 文档中的所有 doctest，这将确保您的示例正常工作。

    为了指示输出结果被截断，您可以在检查应停止的行写上 `[...]`。这在隐藏堆栈跟踪（其中包含对 Julia 代码行的非永久引用）时非常有用，例如当 doctest 显示抛出异常时：

    ````julia
    ```jldoctest
    julia> div(1, 0)
    ERROR: DivideError: integer division error
    [...]
    ```
    ````

    示例如果无法测试，应写在以 ````` ```julia````` 开头的代码块中，以便在生成的文档中正确高亮显示。

    !!! tip
        尽可能的例子应该是**自包含**和**可运行**的，以便读者能够尝试它们，而不必包含任何依赖项。
7. 使用反引号来标识代码和方程式。

    Julia 标识符和代码片段应始终放在反引号 ``` ` ``` 之间以启用高亮显示。可以在双反引号 ``` `` ``` 之间插入 LaTeX 语法的方程式。使用 Unicode 字符而不是它们的 LaTeX 转义序列，即 ``` ``α = 1`` ``` 而不是 ``` ``\\alpha = 1`` ```.
8. Place the starting and ending `"""` characters on lines by themselves.

    请写：

    ```julia
    """
    ...

    ...
    """
    f(x, y) = ...
    ```

    而不是：

    ```julia
    """...

    ..."""
    f(x, y) = ...
    ```

    这使得文档字符串的开始和结束更加清晰。
9. 尊重周围代码中使用的行长度限制。

    文档字符串的编辑使用与代码相同的工具。因此，应该适用相同的约定。建议每行最多宽度为92个字符。
10. 提供信息以允许自定义类型实现`# 实现`部分中的函数。这些实现细节是针对开发人员而非用户，解释例如应该重写哪些函数以及哪些函数自动使用适当的后备。此类细节最好与函数行为的主要描述分开。
11. 对于较长的文档字符串，请考虑使用 `# 扩展帮助` 标头来拆分文档。典型的帮助模式只会显示标头上方的内容；您可以通过在表达式前添加一个 '?' 来访问完整的帮助（即，使用 "??foo" 而不是 "?foo"）。

## Functions & Methods

在Julia中，函数可以有多个实现，称为方法。虽然通用函数最好只有一个目的，但如果有必要，Julia允许单独记录方法。一般来说，只有最通用的方法应该被记录，甚至是函数本身（即通过`function bar end`创建的没有任何方法的对象）。只有当特定方法的行为与更通用的方法不同时，才应该记录它们。在任何情况下，它们不应重复其他地方提供的信息。例如：

```julia
"""
    *(x, y, z...)

Multiplication operator. `x * y * z *...` calls this function with multiple
arguments, i.e. `*(x, y, z...)`.
"""
function *(x, y, z...)
    # ... [implementation sold separately] ...
end

"""
    *(x::AbstractString, y::AbstractString, z::AbstractString...)

When applied to strings, concatenates them.
"""
function *(x::AbstractString, y::AbstractString, z::AbstractString...)
    # ... [insert secret sauce here] ...
end

help?> *
search: * .*

  *(x, y, z...)

  Multiplication operator. x * y * z *... calls this function with multiple
  arguments, i.e. *(x,y,z...).

  *(x::AbstractString, y::AbstractString, z::AbstractString...)

  When applied to strings, concatenates them.
```

当检索通用函数的文档时，每个方法的元数据通过 `catdoc` 函数连接在一起，当然可以为自定义类型覆盖该函数。

## Advanced Usage

`@doc` 宏将其第一个参数与第二个参数关联在一个名为 `META` 的每模块字典中。

为了更容易编写文档，解析器特别处理宏名称 `@doc`：如果对 `@doc` 的调用只有一个参数，但在单行换行后出现另一个表达式，则该额外表达式将作为参数添加到宏中。因此，以下语法被解析为对 `@doc` 的两个参数调用：

```julia
@doc raw"""
...
"""
f(x) = x
```

这使得可以使用除了普通字符串字面量（例如 `raw""` 字符串宏）之外的表达式作为文档字符串。

当用于检索文档时，`@doc` 宏（或同样的，`doc` 函数）将搜索所有 `META` 字典以查找与给定对象相关的元数据并返回它。返回的对象（例如一些 Markdown 内容）默认会智能地显示自己。这个设计也使得以编程方式使用文档系统变得简单；例如，可以在不同版本的函数之间重用文档：

```julia
@doc "..." foo!
@doc (@doc foo!) foo
```

或用于 Julia 的元编程功能：

```julia
for (f, op) in ((:add, :+), (:subtract, :-), (:multiply, :*), (:divide, :/))
    @eval begin
        $f(a, b) = $op(a, b)
    end
end
@doc "`add(a, b)` adds `a` and `b` together" add
@doc "`subtract(a, b)` subtracts `b` from `a`" subtract
```

在非顶层块中的文档，例如 `begin`、`if`、`for`、`let` 和内部构造函数，也应通过 `@doc` 添加到文档系统中。例如：

```julia
if condition()
    @doc "..."
    f(x) = x
end
```

将在 `condition()` 为 `true` 时添加文档到 `f(x)`。请注意，即使 `f(x)` 在一个块的末尾超出作用域，其文档仍将保留。

可以利用元编程来帮助创建文档。在文档字符串中使用字符串插值时，您需要使用额外的 `$`，如 `$($name)` 所示：

```julia
for func in (:day, :dayofmonth)
    name = string(func)
    @eval begin
        @doc """
            $($name)(dt::TimeType) -> Int64

        The day of month of a `Date` or `DateTime` as an `Int64`.
        """ $func(dt::Dates.TimeType)
    end
end
```

### Dynamic documentation

有时，某个类型实例的适当文档取决于该实例的字段值，而不仅仅是类型本身。在这些情况下，您可以为自定义类型向 `Docs.getdoc` 添加一个方法，该方法根据每个实例返回文档。例如，

```julia
struct MyType
    value::Int
end

Docs.getdoc(t::MyType) = "Documentation for MyType with value $(t.value)"

x = MyType(1)
y = MyType(2)
```

`?x` 将显示 "MyType 值为 1 的文档"，而 `?y` 将显示 "MyType 值为 2 的文档"。

## Syntax Guide

本指南提供了如何将文档附加到所有可以提供文档的Julia语法结构的全面概述。

在以下示例中，`"..."` 用于说明一个任意的文档字符串。

### `$` and `\` characters

`$` 和 `\` 字符在文档字符串中仍然被解析为字符串插值或转义序列的开始。可以使用 `raw""` 字符串宏和 `@doc` 宏来避免必须转义它们。当文档字符串包含 LaTeX 或 Julia 源代码示例时，这非常方便：

````julia
@doc raw"""
```math
\LaTeX
```
"""
function f end
````

### Functions and Methods

```julia
"..."
function f end

"..."
f
```

为函数 `f` 添加文档字符串 `"..."`。首个版本是首选语法，但两者是等效的。

```julia
"..."
f(x) = x

"..."
function f(x)
    return x
end

"..."
f(x)
```

为方法 `f(::Any)` 添加文档字符串 `"..."`。

```julia
"..."
f(x, y = 1) = x + y
```

为两个 `Method` 添加文档字符串 `"..."`，即 `f(::Any)` 和 `f(::Any, ::Any)`。

### Macros

```julia
"..."
macro m(x) end
```

在 `@m(::Any)` 宏定义中添加文档字符串 `"..."`。

```julia
"..."
:(@m1)

"..."
macro m2 end
```

为名为 `@m1` 和 `@m2` 的宏添加文档字符串 `"..."`。

### Types

```
"..."
abstract type T1 end

"..."
mutable struct T2
    ...
end

"..."
struct T3
    ...
end
```

为类型 `T1`、`T2` 和 `T3` 添加文档字符串 `"..."`。

```
"..."
T1

"..."
T2

"..."
T3
```

将文档字符串 `"..."` 添加到类型 `T1`、`T2` 和 `T3`。之前的版本是首选语法，但两者是等效的。

```julia
"..."
struct T
    "x"
    x
    "y"
    y

    @doc "Inner constructor"
    function T()
        new(...)
    end
end
```

为类型 `T` 添加文档字符串 `"..."`，为字段 `T.x` 添加 `"x"`，为字段 `T.y` 添加 `"y"`，并为内部构造函数 `T()` 添加 `"Inner constructor"`。同样适用于 `mutable struct` 类型。

### Modules

```julia
"..."
module M end

module M

"..."
M

end
```

为 `Module` `M` 添加文档字符串 `"..."`。将文档字符串放在 `Module` 之上是首选语法，但两者是等效的。

```julia
"..."
baremodule M
# ...
end

baremodule M

import Base: @doc

"..."
f(x) = x

end
```

通过在表达式上方放置文档字符串来记录 `baremodule`，会自动将 `@doc` 导入到模块中。当模块表达式未被记录时，这些导入必须手动完成。

### Global Variables

```julia
"..."
const a = 1

"..."
b = 2

"..."
global c = 3
```

为 `Binding` 的 `a`、`b` 和 `c` 添加文档字符串 `"..."`。

`Binding`用于在`Module`中存储对特定`Symbol`的引用，而不存储被引用的值本身。

!!! note
    当 `const` 定义仅用于定义另一个定义的别名时，例如在 `Base` 中的函数 `div` 和它的别名 `÷`，请不要记录别名，而是记录实际的函数。

    如果别名已被记录且不是实际定义，那么文档系统（`?` 模式）在搜索实际定义时将不会返回附加到别名的文档字符串。

    例如你应该写

    ```julia
    "..."
    f(x) = x + 1
    const alias = f
    ```

    而不是

    ```julia
    f(x) = x + 1
    "..."
    const alias = f
    ```


```julia
"..."
sym
```

为与 `sym` 关联的值添加文档字符串 `"..."`。但是，最好在定义 `sym` 的地方进行文档说明。

### Multiple Objects

```julia
"..."
a, b
```

将文档字符串 `"..."` 添加到 `a` 和 `b`，每个都应该是一个可文档化的表达式。此语法等同于

```julia
"..."
a

"..."
b
```

可以以这种方式一起记录任意数量的表达式。当两个函数相关时，例如非变异版本和变异版本 `f` 和 `f!`，这种语法可能会很有用。

### Macro-generated code

```julia
"..."
@m expression
```

将文档字符串 `"..."` 添加到通过扩展 `@m expression` 生成的表达式中。这允许使用 `@inline`、`@noinline`、`@generated` 或任何其他宏装饰的表达式以与未装饰表达式相同的方式进行文档化。

宏作者应注意，只有生成单个表达式的宏才会自动支持文档字符串。如果宏返回一个包含多个子表达式的块，则需要文档化的子表达式必须使用 [`@__doc__`](@ref Core.@__doc__) 宏进行标记。

[`@enum`](@ref) 宏利用 `@__doc__` 来允许对 [`Enum`](@ref) 进行文档编写。检查其定义应作为如何正确使用 `@__doc__` 的示例。

```@docs
Core.@__doc__
```
