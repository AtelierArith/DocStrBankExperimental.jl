# Julia Functions

本文将解释函数、方法定义和方法表是如何工作的。

## Method Tables

在Julia中，每个函数都是一个泛型函数。泛型函数在概念上是一个单一的函数，但由许多定义或方法组成。泛型函数的方法存储在方法表中。方法表（类型为`MethodTable`）与`TypeName`相关联。`TypeName`描述了一组参数化类型。例如，`Complex{Float32}`和`Complex{Float64}`共享相同的`Complex`类型名称对象。

在Julia中，所有对象都是潜在可调用的，因为每个对象都有一个类型，而这个类型又有一个`TypeName`。

## [Function calls](@id Function-calls)

给定调用 `f(x, y)`，执行以下步骤：首先，访问要使用的方法表，作为 `typeof(f).name.mt`。其次，形成一个参数元组类型 `Tuple{typeof(f), typeof(x), typeof(y)}`。请注意，函数本身的类型是第一个元素。这是因为类型可能具有参数，因此需要参与调度。这个元组类型在方法表中查找。

此调度过程由 `jl_apply_generic` 执行，它接受两个参数：指向值数组 `f`、`x` 和 `y` 的指针，以及值的数量（在这种情况下为 3）。

在整个系统中，有两种类型的 API 处理函数和参数列表：一种是分别接受函数和参数的，另一种是接受单一参数结构的。在第一种 API 中，“参数”部分*不*包含关于函数的信息，因为函数是单独传递的。在第二种 API 中，函数是参数结构的第一个元素。

例如，以下执行调用的函数仅接受一个 `args` 指针，因此 args 数组的第一个元素将是要调用的函数：

```c
jl_value_t *jl_apply(jl_value_t **args, uint32_t nargs)
```

此入口点为相同功能单独接受函数，因此 `args` 数组不包含该函数：

```c
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs);
```

## Adding methods

根据上述调度过程，从概念上讲，添加新方法所需的只是 (1) 一个元组类型，以及 (2) 方法主体的代码。`jl_method_def` 实现了这个操作。`jl_method_table_for` 被调用以从第一个参数的类型中提取相关的方法表。这比调度期间的相应过程复杂得多，因为参数元组类型可能是抽象的。例如，我们可以定义：

```julia
(::Union{Foo{Int},Foo{Int8}})(x) = 0
```

这有效，因为所有可能的匹配方法都将属于同一个方法表。

## Creating generic functions

由于每个对象都是可调用的，因此创建一个通用函数不需要特别的操作。因此 `jl_new_generic_function` 只是创建一个新的单例（0 大小）`Function` 的子类型并返回其实例。一个函数可以有一个助记符“显示名称”，用于调试信息和打印对象时。例如，`Base.sin` 的名称是 `sin`。根据约定，创建的 *类型* 的名称与函数名称相同，前面加上 `#`。因此 `typeof(sin)` 是 `Base.#sin`。

## Closures

闭包只是一个可调用对象，其字段名称对应于捕获的变量。例如，以下代码：

```julia
function adder(x)
    return y->x+y
end
```

降低到（大约）：

```julia
struct ##1{T}
    x::T
end

(_::##1)(y) = _.x + y

function adder(x)
    return ##1(x)
end
```

## Constructors

构造函数调用只是对一个类型的调用。`Type` 的方法表包含所有构造函数定义。`Type` 的所有子类型（`Type`、`UnionAll`、`Union` 和 `DataType`）目前通过特殊安排共享一个方法表。

## Builtins

在 `Core` 模块中定义的“内置”函数是：

```@eval
function lines(words)
    io = IOBuffer()
    n = 0
    for w in words
        if n+length(w) > 80
            print(io, '\n', w)
            n = length(w)
        elseif n == 0
            print(io, w);
            n += length(w)
        else
            print(io, ' ', w);
            n += length(w)+1
        end
    end
    String(take!(io))
end
import Markdown
[string(n) for n in names(Core;all=true)
    if getfield(Core,n) isa Core.Builtin && nameof(getfield(Core,n)) === n] |>
    lines |>
    s ->  "```\n$s\n```" |>
    Markdown.parse
```

这些都是单例对象，其类型是 `Builtin` 的子类型，而 `Builtin` 又是 `Function` 的子类型。它们的目的是在运行时暴露使用 "jlcall" 调用约定的入口点：

```c
jl_value_t *(jl_value_t*, jl_value_t**, uint32_t)
```

内置方法表是空的。相反，它们有一个通用的方法缓存条目（`Tuple{Vararg{Any}}`），其 jlcall fptr 指向正确的函数。这有点像一种 hack，但效果相当不错。

## Keyword arguments

关键字参数通过向 kwcall 函数添加方法来工作。这个函数通常是“关键字参数排序器”或“关键字排序器”，然后调用函数的内部主体（匿名定义）。在 kwsorter 函数中的每个定义都具有与正常方法表中的某个定义相同的参数，除了前面添加了一个 `NamedTuple` 参数，该参数提供了传递的关键字参数的名称和值。kwsorter 的工作是根据名称将关键字参数移动到其规范位置，并评估和替换任何需要的默认值表达式。结果是一个正常的位置参数列表，然后传递给另一个编译器生成的函数。

理解这个过程最简单的方法是查看关键字参数方法定义是如何被降低的。代码：

```julia
function circle(center, radius; color = black, fill::Bool = true, options...)
    # draw
end
```

实际上生成了 *三个* 方法定义。第一个是一个接受所有参数（包括关键字参数）作为位置参数的函数，并包含方法体的代码。它具有自动生成的名称：

```julia
function #circle#1(color, fill::Bool, options, circle, center, radius)
    # draw
end
```

第二种方法是对原始 `circle` 函数的普通定义，它处理没有传递关键字参数的情况：

```julia
function circle(center, radius)
    #circle#1(black, true, pairs(NamedTuple()), circle, center, radius)
end
```

这只是简单地调用第一个方法，并传递默认值。`pairs` 被应用于命名元组的剩余参数，以提供键值对迭代。请注意，如果该方法不接受剩余关键字参数，则该参数将缺失。

最后是 kwsorter 的定义：

```
function (::Core.kwftype(typeof(circle)))(kws, circle, center, radius)
    if haskey(kws, :color)
        color = kws.color
    else
        color = black
    end
    # etc.

    # put remaining kwargs in `options`
    options = structdiff(kws, NamedTuple{(:color, :fill)})

    # if the method doesn't accept rest keywords, throw an error
    # unless `options` is empty

    #circle#1(color, fill, pairs(options), circle, center, radius)
end
```

函数 `Core.kwftype(t)` 创建字段 `t.name.mt.kwsorter`（如果尚未创建），并返回该函数的类型。

此设计的特点是，未使用关键字参数的调用站点无需特殊处理；一切都像它们根本不是语言的一部分一样工作。使用关键字参数的调用站点会直接调度到被调用函数的 kwsorter。例如，调用：

```julia
circle((0, 0), 1.0, color = red; other...)
```

降低到：

```julia
kwcall(merge((color = red,), other), circle, (0, 0), 1.0)
```

`kwcall`（也在`Core`中）表示一个kwcall签名和调度。关键字展开操作（写作`other...`）调用命名元组`merge`函数。该函数进一步解包`other`的每个*元素*，期望每个元素包含两个值（一个符号和一个值）。自然地，如果所有展开的参数都是命名元组，则可以提供更高效的实现。请注意，原始的`circle`函数被传递，以处理闭包。

## [Compiler efficiency issues](@id compiler-efficiency-issues)

为每个函数生成一个新类型在与Julia的“默认对所有参数进行特化”设计结合时，可能会对编译器资源使用产生严重后果。实际上，这一设计的初始实现遭遇了更长的构建和测试时间、更高的内存使用，以及一个几乎是基线大小2倍的系统映像。在一个天真的实现中，这个问题严重到几乎使系统无法使用。需要进行几项重要的优化才能使该设计变得实用。

第一个问题是对不同函数值参数的过度专门化。许多函数只是将一个参数“传递”到其他地方，例如传递给另一个函数或存储位置。这些函数不需要针对可能传入的每个闭包进行专门化。幸运的是，这种情况很容易区分，只需考虑一个函数是否*调用*了它的一个参数（即该参数在某个地方出现在“头部位置”）。性能关键的高阶函数如 `map` 确实会调用它们的参数函数，因此仍然会按预期进行专门化。此优化通过在前端的 `analyze-variables` 过程中记录哪些参数被调用来实现。当 `cache_method` 看到传递给声明为 `Any` 或 `Function` 的槽的 `Function` 类型层次中的一个参数时，它的行为就像应用了 `@nospecialize` 注释。这种启发式方法在实践中似乎非常有效。

下一个问题涉及方法缓存哈希表的结构。实证研究表明，绝大多数动态调度调用涉及一个或两个参数。反过来，这些情况中的许多可以仅通过考虑第一个参数来解决。（顺便提一下，单调度的支持者对此并不会感到惊讶。然而，这个论点意味着“多重调度在实践中容易优化”，因此我们应该使用它，而不是“我们应该使用单调度”！）因此，方法缓存使用第一个参数的类型作为其主键。请注意，这对应于函数调用的元组类型的*第二*个元素（第一个元素是函数本身的类型）。通常，头位置的类型变化极低——实际上，大多数函数属于没有参数的单例类型。然而，对于构造函数情况并非如此，其中一个方法表保存每种类型的构造函数。因此，`Type`方法表被特殊处理，以使用*第一个*元组类型元素而不是第二个。

前端为所有闭包生成类型声明。最初，这是通过生成普通类型声明来实现的。然而，这产生了大量的构造函数，所有这些构造函数都是微不足道的（只是将所有参数传递给 [`new`](@ref)）。由于方法是部分有序的，插入所有这些方法的复杂度是 O(n²)，而且它们的数量太多，无法保留。通过直接生成 `struct_type` 表达式（绕过默认构造函数生成）并直接使用 `new` 创建闭包实例，这一过程得到了优化。这并不是最美观的做法，但你必须这样做。

下一个问题是 `@test` 宏，它为每个测试用例生成了一个 0 参数的闭包。这实际上并不是必要的，因为每个测试用例只需在原地运行一次。因此，`@test` 被修改为扩展为一个 try-catch 块，该块记录测试结果（真、假或引发的异常）并在其上调用测试套件处理程序。
