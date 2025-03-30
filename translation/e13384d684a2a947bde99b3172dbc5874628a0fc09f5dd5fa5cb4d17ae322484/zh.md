# Talking to the compiler (the `:meta` mechanism)

在某些情况下，您可能希望提供提示或指令，表明给定的代码块具有特殊属性：您可能总是希望将其内联，或者您可能希望启用特殊的编译器优化过程。从版本 0.4 开始，Julia 采用了一种约定，这些指令可以放置在 `:meta` 表达式中，通常（但不一定）是函数主体中的第一个表达式。

`:meta` 表达式是通过宏创建的。作为一个例子，考虑 `@inline` 宏的实现：

```julia
macro inline(ex)
    esc(isa(ex, Expr) ? pushmeta!(ex, :inline) : ex)
end
```

在这里，`ex` 预计是一个定义函数的表达式。像这样的语句：

```julia
@inline function myfunction(x)
    x*(x+3)
end
```

变成一个像这样的表达式：

```julia
quote
    function myfunction(x)
        Expr(:meta, :inline)
        x*(x+3)
    end
end
```

`Base.pushmeta!(ex, tag::Union{Symbol,Expr})` 将 `:tag` 附加到 `:meta` 表达式的末尾，如果必要的话会创建一个新的 `:meta` 表达式。

要使用元数据，您必须解析这些 `:meta` 表达式。如果您的实现可以在 Julia 中执行，`Base.popmeta!` 非常方便：`Base.popmeta!(body, :symbol)` 将扫描一个函数 *body* 表达式（没有函数签名的表达式），查找第一个包含 `:symbol` 的 `:meta` 表达式，提取任何参数，并返回一个元组 `(found::Bool, args::Array{Any})`。如果元数据没有任何参数，或者没有找到 `:symbol`，则 `args` 数组将为空。

尚未提供的是一个方便的基础设施，用于解析 C++ 中的 `:meta` 表达式。
