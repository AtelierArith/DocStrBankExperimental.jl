```
@NamedTuple{key1::Type1, key2::Type2, ...}
@NamedTuple begin key1::Type1; key2::Type2; ...; end
```

这个宏提供了一种更方便的语法来声明 `NamedTuple` 类型。它返回一个具有给定键和类型的 `NamedTuple` 类型，相当于 `NamedTuple{(:key1, :key2, ...), Tuple{Type1,Type2,...}}`。如果省略 `::Type` 声明，则默认为 `Any`。`begin ... end` 形式允许将声明分布在多行（类似于 `struct` 声明），但在其他方面是等效的。`NamedTuple` 宏在打印 `NamedTuple` 类型时使用，例如在 REPL 中。

例如，元组 `(a=3.1, b="hello")` 的类型是 `NamedTuple{(:a, :b), Tuple{Float64, String}}`，也可以通过 `@NamedTuple` 声明为：

```jldoctest
julia> @NamedTuple{a::Float64, b::String}
@NamedTuple{a::Float64, b::String}

julia> @NamedTuple begin
           a::Float64
           b::String
       end
@NamedTuple{a::Float64, b::String}
```

!!! compat "Julia 1.5"
    该宏自 Julia 1.5 起可用。

