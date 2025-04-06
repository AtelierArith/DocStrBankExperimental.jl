```
函数
```

所有函数的抽象类型。

# 示例

```jldoctest
julia> isa(+, Function)
true

julia> typeof(sin)
typeof(sin) (函数 sin 的单例类型，Function 的子类型)

julia> ans <: Function
true
```
