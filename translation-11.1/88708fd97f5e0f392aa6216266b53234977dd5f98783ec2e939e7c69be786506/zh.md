# Base.Cartesian

该（未导出的）Cartesian模块提供了宏，便于编写多维算法。通常情况下，您可以使用 [straightforward techniques](https://julialang.org/blog/2016/02/iteration) 来编写此类算法；然而，在某些情况下，`Base.Cartesian` 仍然是有用或必要的。

## Principles of usage

一个简单的用法示例是：

```julia
@nloops 3 i A begin
    s += @nref 3 A i
end
```

生成以下代码：

```julia
for i_3 = axes(A, 3)
    for i_2 = axes(A, 2)
        for i_1 = axes(A, 1)
            s += A[i_1, i_2, i_3]
        end
    end
end
```

一般来说，Cartesian 允许您编写包含重复元素的通用代码，例如此示例中的嵌套循环。其他应用包括重复表达式（例如，循环展开）或在不使用 "splat" 构造（`i...`）的情况下创建具有可变参数数量的函数调用。

## Basic syntax

`@nloops` 的（基本）语法如下：

  * 第一个参数必须是一个整数（*不是*变量），指定循环的次数。
  * 第二个参数是用于迭代器变量的符号前缀。这里我们使用了 `i`，并生成了变量 `i_1, i_2, i_3`。
  * 第三个参数指定了每个迭代器变量的范围。如果在这里使用一个变量（符号），它将被视为 `axes(A, dim)`。更灵活地，你可以使用下面描述的匿名函数表达式语法。
  * 最后一个参数是循环的主体。在这里，这就是出现在 `begin...end` 之间的内容。

`@nloops` 的一些附加功能在 [reference section](@ref dev-cartesian-reference) 中进行了描述。

`@nref` 遵循类似的模式，从 `@nref 3 A i` 生成 `A[i_1,i_2,i_3]`。一般的做法是从左到右读取，这就是为什么 `@nloops` 是 `@nloops 3 i A expr`（如 `for i_2 = axes(A, 2)`，其中 `i_2` 在左边，范围在右边），而 `@nref` 是 `@nref 3 A i`（如 `A[i_1,i_2,i_3]`，其中数组在前）。

如果您正在使用 Cartesian 开发代码，您可能会发现通过使用 `@macroexpand` 检查生成的代码可以更容易地进行调试：

```@meta
DocTestSetup = quote
    import Base.Cartesian: @nref
end
```

```jldoctest
julia> @macroexpand @nref 2 A i
:(A[i_1, i_2])
```

```@meta
DocTestSetup = nothing
```

### Supplying the number of expressions

这两个宏的第一个参数是表达式的数量，必须是一个整数。当你编写一个打算在多个维度中工作的函数时，这可能不是你想要硬编码的内容。推荐的方法是使用 `@generated function`。以下是一个示例：

```julia
@generated function mysum(A::Array{T,N}) where {T,N}
    quote
        s = zero(T)
        @nloops $N i A begin
            s += @nref $N A i
        end
        s
    end
end
```

当然，您也可以在 `quote` 块之前准备表达式或进行计算。

### Anonymous-function expressions as macro arguments

`Cartesian` 中最强大的功能之一可能是能够提供在解析时被评估的匿名函数表达式。让我们考虑一个简单的例子：

```julia
@nexprs 2 j->(i_j = 1)
```

`@nexprs` 生成 `n` 个遵循某种模式的表达式。此代码将生成以下语句：

```julia
i_1 = 1
i_2 = 1
```

在每个生成的语句中，一个“孤立的”`j`（匿名函数的变量）被替换为范围`1:2`中的值。一般来说，Cartesian使用类似LaTeX的语法。这使得你可以对索引`j`进行数学运算。以下是计算数组步幅的示例：

```julia
s_1 = 1
@nexprs 3 j->(s_{j+1} = s_j * size(A, j))
```

将生成表达式

```julia
s_1 = 1
s_2 = s_1 * size(A, 1)
s_3 = s_2 * size(A, 2)
s_4 = s_3 * size(A, 3)
```

匿名函数表达式在实践中有许多用途。

#### [Macro reference](@id dev-cartesian-reference)

```@docs
Base.Cartesian.@nloops
Base.Cartesian.@nref
Base.Cartesian.@nextract
Base.Cartesian.@nexprs
Base.Cartesian.@ncall
Base.Cartesian.@ncallkw
Base.Cartesian.@ntuple
Base.Cartesian.@nall
Base.Cartesian.@nany
Base.Cartesian.@nif
```
