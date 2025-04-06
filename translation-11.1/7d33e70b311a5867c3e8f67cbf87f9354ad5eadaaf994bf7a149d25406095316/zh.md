```
@enum EnumName[::BaseType] value1[=x] value2[=y]
```

创建一个名为 `EnumName` 的 `Enum{BaseType}` 子类型，枚举成员值为 `value1` 和 `value2`，可选的赋值为 `x` 和 `y`。`EnumName` 可以像其他类型一样使用，枚举成员值可以作为常规值使用，例如

# 示例

```jldoctest fruitenum
julia> @enum Fruit apple=1 orange=2 kiwi=3

julia> f(x::Fruit) = "I'm a Fruit with value: $(Int(x))"
f (generic function with 1 method)

julia> f(apple)
"I'm a Fruit with value: 1"

julia> Fruit(1)
apple::Fruit = 1
```

值也可以在 `begin` 块内指定，例如

```julia
@enum EnumName begin
    value1
    value2
end
```

`BaseType` 默认为 [`Int32`](@ref)，必须是 `Integer` 的原始子类型。成员值可以在枚举类型和 `BaseType` 之间转换。`read` 和 `write` 会自动执行这些转换。如果枚举是使用非默认的 `BaseType` 创建的，`Integer(value1)` 将返回类型为 `BaseType` 的整数 `value1`。

要列出枚举的所有实例，请使用 `instances`，例如

```jldoctest fruitenum
julia> instances(Fruit)
(apple, orange, kiwi)
```

可以从枚举实例构造符号：

```jldoctest fruitenum
julia> Symbol(apple)
:apple
```
