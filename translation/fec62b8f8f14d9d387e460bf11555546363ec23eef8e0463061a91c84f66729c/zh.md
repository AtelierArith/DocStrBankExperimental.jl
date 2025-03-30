```
where
```

`where` 关键字创建一个 [`UnionAll`](@ref) 类型，可以被视为对某个变量的所有值进行的其他类型的迭代联合。例如 `Vector{T} where T<:Real` 包含所有元素类型为某种 `Real` 数字的 [`Vector`](@ref)。

如果省略变量绑定，默认绑定为 [`Any`](@ref)：

```julia
Vector{T} where T    # 简写为 `where T<:Any`
```

变量也可以有下界：

```julia
Vector{T} where T>:Int
Vector{T} where Int<:T<:Real
```

对于嵌套的 `where` 表达式，还有一种简洁的语法。例如，这个：

```julia
Pair{T, S} where S<:Array{T} where T<:Number
```

可以简化为：

```julia
Pair{T, S} where {T<:Number, S<:Array{T}}
```

这种形式通常出现在方法签名中。

请注意，在这种形式中，变量按外层优先的顺序列出。这与使用语法 `T{p1, p2, ...}` 将类型“应用”到参数值时变量的替换顺序相匹配。
