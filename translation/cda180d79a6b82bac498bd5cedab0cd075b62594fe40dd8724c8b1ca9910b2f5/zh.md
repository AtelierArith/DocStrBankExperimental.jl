```
Tuple{Types...}
```

元组是一个固定长度的容器，可以容纳不同类型的任何值，但不能被修改（它是不可变的）。可以通过索引访问这些值。元组字面量用逗号和括号表示：

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"

julia> typeof(x)
Tuple{Float64, String, Int64}
```

长度为1的元组必须用逗号书写，即`(1,)`，因为`(1)`只是一个带括号的值。`()`表示空（长度为0）元组。

可以通过使用`Tuple`类型作为构造函数从迭代器构造元组：

```jldoctest
julia> Tuple(["a", 1])
("a", 1)

julia> Tuple{String, Float64}(["a", 1])
("a", 1.0)
```

元组类型在其参数中是协变的：`Tuple{Int}`是`Tuple{Any}`的子类型。因此，`Tuple{Any}`被视为抽象类型，只有当其参数是具体的时，元组类型才是具体的。元组没有字段名称；字段只能通过索引访问。元组类型可以有任意数量的参数。

请参阅手册中关于[Tuple Types](@ref)的部分。

另请参阅[`Vararg`](@ref)、[`NTuple`](@ref)、[`ntuple`](@ref)、[`tuple`](@ref)、[`NamedTuple`](@ref)。
