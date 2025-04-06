```
AnnotatedString{S <: AbstractString} <: AbstractString
```

带有元数据的字符串，以注释区域的形式呈现。

更具体地说，这是对任何其他 [`AbstractString`](@ref) 的简单包装，允许将被包装字符串的区域注释为带标签的值。

```text
                           C
                    ┌──────┸─────────┐
  "this is an example annotated string"
  └──┰────────┼─────┘         │
     A        └─────┰─────────┘
                    B
```

上面的图表示一个 `AnnotatedString`，其中三个范围已被注释（标记为 `A`、`B` 和 `C`）。每个注释包含一个标签（`Symbol`）和一个值（`Any`）。这三条信息作为 `@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}` 保存。

标签不需要唯一，相同的区域可以持有多个具有相同标签的注释。

为 `AnnotatedString` 编写的代码通常应保持以下属性：

  * 注释应用于哪些字符
  * 注释应用于每个字符的顺序

特定使用 `AnnotatedString` 可能会引入额外的语义。

这些规则的一个推论是，相邻、连续放置的具有相同标签和值的注释等同于一个跨越组合范围的单个注释。

另请参见 [`AnnotatedChar`](@ref)、[`annotatedstring`](@ref)、[`annotations`](@ref) 和 [`annotate!`](@ref)。

# 构造函数

```julia
AnnotatedString(s::S<:AbstractString) -> AnnotatedString{S}
AnnotatedString(s::S<:AbstractString, annotations::Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}})
```

也可以使用 [`annotatedstring`](@ref) 创建 `AnnotatedString`，它的作用类似于 [`string`](@ref)，但保留参数中存在的任何注释。

# 示例

```julia-repl
julia> AnnotatedString("this is an example annotated string",
                    [(1:18, :A => 1), (12:28, :B => 2), (18:35, :C => 3)])
"this is an example annotated string"
```
