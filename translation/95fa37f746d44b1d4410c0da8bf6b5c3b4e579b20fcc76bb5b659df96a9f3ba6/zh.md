```
AnnotatedChar{S <: AbstractChar} <: AbstractChar
```

带注释的字符。

更具体地说，这是一个简单的包装器，围绕任何其他 [`AbstractChar`](@ref)，它与被包装的字符一起保存一组任意标记的注释（`@NamedTuple{label::Symbol, value}`）。

另请参见：[`AnnotatedString`](@ref)，[`annotatedstring`](@ref)，`annotations` 和 `annotate!`。

# 构造函数

```julia
AnnotatedChar(s::S) -> AnnotatedChar{S}
AnnotatedChar(s::S, annotations::Vector{@NamedTuple{label::Symbol, value}})
```

# 示例

```julia-repl
julia> AnnotatedChar('j', :label => 1)
'j': ASCII/Unicode U+006A (category Ll: Letter, lowercase)
```
