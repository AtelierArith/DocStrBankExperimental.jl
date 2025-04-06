# Reflection and introspection

Julia 提供了多种运行时反射功能。

## Module bindings

`Module` 的公共名称可以通过 [`names(m::Module)`](@ref) 获取，这将返回一个包含 [`Symbol`](@ref) 元素的数组，表示公共绑定。`names(m::Module, all = true)` 返回 `m` 中所有绑定的符号，无论其公共状态如何。

## DataType fields

`DataType` 字段的名称可以使用 [`fieldnames`](@ref) 进行查询。例如，给定以下类型，`fieldnames(Point)` 返回一个元组，包含 [`Symbol`](@ref)，表示字段名称：

```jldoctest struct_point
julia> struct Point
           x::Int
           y
       end

julia> fieldnames(Point)
(:x, :y)
```

`Point` 对象中每个字段的类型存储在 `Point` 变量本身的 `types` 字段中：

```jldoctest struct_point
julia> Point.types
svec(Int64, Any)
```

虽然 `x` 被注解为 `Int`，但 `y` 在类型定义中没有注解，因此 `y` 默认为 `Any` 类型。

类型本身被表示为一个名为 `DataType` 的结构：

```jldoctest struct_point
julia> typeof(Point)
DataType
```

请注意，`fieldnames(DataType)` 返回 `DataType` 本身每个字段的名称，其中一个字段是上面示例中观察到的 `types` 字段。

## Subtypes

任何 `DataType` 的 *直接* 子类型可以使用 [`subtypes`](@ref) 列出。例如，抽象 `DataType` [`AbstractFloat`](@ref) 具有四个（具体的）子类型：

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.subtypes(AbstractFloat)
5-element Vector{Any}:
 BigFloat
 Core.BFloat16
 Float16
 Float32
 Float64
```

任何抽象子类型也将包含在此列表中，但其进一步的子类型将不包括在内；可以递归应用 [`subtypes`](@ref) 来检查完整的类型树。

注意到 [`subtypes`](@ref) 位于 [`InteractiveUtils`](@ref man-interactive-utils) 内部，但在使用 REPL 时会自动导出。

## DataType layout

`DataType` 的内部表示在与 C 代码接口时至关重要，并且有几个函数可用于检查这些细节。 [`isbitstype(T::DataType)`](@ref) 如果 `T` 以 C 兼容的对齐方式存储，则返回 true。 [`fieldoffset(T::DataType, i::Integer)`](@ref) 返回字段 *i* 相对于类型起始位置的（字节）偏移量。

## Function methods

任何通用函数的方法可以使用 [`methods`](@ref) 列出。可以使用 [`methodswith`](@ref) 在方法调度表中搜索接受给定类型的方法。

## Expansion and lowering

As discussed in the [Metaprogramming](@ref) section, the [`macroexpand`](@ref) function gives the unquoted and interpolated expression ([`Expr`](@ref)) form for a given macro. To use `macroexpand`, `quote` the expression block itself (otherwise, the macro will be evaluated and the result will be passed instead!). For example:

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.macroexpand(@__MODULE__, :(@edit println("")) )
:(InteractiveUtils.edit(println, (Base.typesof)("")))
```

函数 `Base.Meta.show_sexpr` 和 [`dump`](@ref) 用于显示 S 表达式风格的视图和深度嵌套的详细视图，适用于任何表达式。

最后，[`Meta.lower`](@ref) 函数给出了任何表达式的 `lowered` 形式，特别有助于理解语言构造如何映射到基本操作，如赋值、分支和调用：

```jldoctest; setup = (using Base: +, sin)
julia> Meta.lower(@__MODULE__, :( [1+2, sin(0.5)] ))
:($(Expr(:thunk, CodeInfo(
    @ none within `top-level scope`
1 ─ %1 = 1 + 2
│   %2 = sin(0.5)
│   %3 = Base.vect(%1, %2)
└──      return %3
))))
```

## Intermediate and compiled representations

检查函数的降级形式需要选择特定的方法进行显示，因为通用函数可能有许多具有不同类型签名的方法。为此，可以使用 [`code_lowered`](@ref) 进行特定于方法的代码降级，而使用 [`code_typed`](@ref) 可以获得类型推断形式。[`code_warntype`](@ref) 为 `4d61726b646f776e2e436f64652822222c2022636f64655f74797065642229_40726566` 的输出添加了高亮。

更接近机器时，可以使用 [`code_llvm`](@ref) 打印函数的 LLVM 中间表示，最后可以使用 [`code_native`](@ref) 获取编译后的机器代码（这将触发任何未被调用过的函数的 JIT 编译/代码生成）。

为了方便，以上函数的宏版本可以接受标准函数调用并自动扩展参数类型：

```julia-repl
julia> @code_llvm +(1,1)
;  @ int.jl:87 within `+`
; Function Attrs: sspstrong uwtable
define i64 @"julia_+_476"(i64 signext %0, i64 signext %1) #0 {
top:
  %2 = add i64 %1, %0
  ret i64 %2
}
```

有关更多信息，请参见 [`@code_lowered`](@ref)，[`@code_typed`](@ref)，[`@code_warntype`](@ref)，[`@code_llvm`](@ref)，和 [`@code_native`](@ref)。

### Printing of debug information

上述函数和宏接受关键字参数 `debuginfo`，该参数控制打印的调试信息级别。

```jldoctest; setup = :(using InteractiveUtils), filter = r"int.jl:\d+"
julia> InteractiveUtils.@code_typed debuginfo=:source +(1,1)
CodeInfo(
    @ int.jl:87 within `+`
1 ─ %1 = Base.add_int(x, y)::Int64
└──      return %1
) => Int64
```

`debuginfo` 的可能值为：`:none`、`:source` 和 `:default`。默认情况下，不会打印调试信息，但可以通过设置 `Base.IRShow.default_debuginfo[] = :source` 来更改。
