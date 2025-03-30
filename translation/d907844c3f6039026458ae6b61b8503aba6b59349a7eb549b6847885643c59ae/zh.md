```
命名元组
```

`NamedTuple` 是命名 [`Tuple`](@ref) 的集合。也就是说，它们是一个类似元组的值集合，其中每个条目都有一个唯一的名称，表示为 [`Symbol`](@ref)。与 `Tuple` 一样，`NamedTuple` 是不可变的；构造后，名称和数值都不能就地修改。

可以通过带有键的元组字面量创建命名元组，例如 `(a=1, b=2)`，或者通过在开括号后加分号的元组字面量，例如 `(; a=1, b=2)`（这种形式也接受下面描述的程序生成的名称），或者使用 `NamedTuple` 类型作为构造函数，例如 `NamedTuple{(:a, :b)}((1,2))`。

可以使用字段访问语法访问命名元组中与名称相关联的值，例如 `x.a`，或使用 [`getindex`](@ref)，例如 `x[:a]` 或 `x[(:a, :b)]`。可以使用 [`keys`](@ref) 获取名称的元组，使用 [`values`](@ref) 获取值的元组。

!!! note
    对 `NamedTuple` 的迭代会产生 *值* 而不包含名称。（见下面的示例。）要迭代名称-值对，请使用 [`pairs`](@ref) 函数。


[`@NamedTuple`](@ref) 宏可用于方便地声明 `NamedTuple` 类型。

# 示例

```jldoctest
julia> x = (a=1, b=2)
(a = 1, b = 2)

julia> x.a
1

julia> x[:a]
1

julia> x[(:a,)]
(a = 1,)

julia> keys(x)
(:a, :b)

julia> values(x)
(1, 2)

julia> collect(x)
2-element Vector{Int64}:
 1
 2

julia> collect(pairs(x))
2-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
```

以与程序化定义关键字参数类似的方式，可以通过在元组字面量内的分号后给出成对的 `name::Symbol => value` 来创建命名元组。可以混合使用这种和 `name=value` 语法：

```jldoctest
julia> (; :a => 1, :b => 2, c=3)
(a = 1, b = 2, c = 3)
```

名称-值对也可以通过展开命名元组或任何生成两个值集合的迭代器来提供，每个集合的第一个值为符号：

```jldoctest
julia> keys = (:a, :b, :c); values = (1, 2, 3);

julia> NamedTuple{keys}(values)
(a = 1, b = 2, c = 3)

julia> (; (keys .=> values)...)
(a = 1, b = 2, c = 3)

julia> nt1 = (a=1, b=2);

julia> nt2 = (c=3, d=4);

julia> (; nt1..., nt2..., b=20) # 最后的 b 会覆盖 nt1 中的值
(a = 1, b = 20, c = 3, d = 4)

julia> (; zip(keys, values)...) # zip 生成的元组如 (:a, 1)
(a = 1, b = 2, c = 3)
```

与关键字参数一样，标识符和点表达式隐含名称：

```jldoctest
julia> x = 0
0

julia> t = (; x)
(x = 0,)

julia> (; t.x)
(x = 0,)
```

!!! compat "Julia 1.5"
    从标识符和点表达式隐含的名称自 Julia 1.5 起可用。


!!! compat "Julia 1.7"
    使用多个 `Symbol` 的 `getindex` 方法自 Julia 1.7 起可用。

