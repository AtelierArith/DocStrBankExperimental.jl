```
ord(lt, by, rev::Union{Bool, Nothing}, order::Ordering=Forward)
```

从与[`sort!`](@ref)使用的相同参数构造一个[`Ordering`](@ref)对象。元素首先通过函数`by`（可以是[`identity`](@ref)）进行转换，然后根据函数`lt`或现有的排序`order`进行比较。`lt`应该是[`isless`](@ref)或遵循与[`sort!`](@ref)的`lt`参数相同规则的函数。最后，如果`rev=true`，则结果顺序会被反转。

传递一个与`isless`不同的`lt`以及一个与[`Base.Order.Forward`](@ref)或[`Base.Order.Reverse`](@ref)不同的`order`是不允许的，否则所有选项都是独立的，可以在所有可能的组合中一起使用。
