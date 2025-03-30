```
@with (var::ScopedValue{T} => val)... expr
```

`with` 的宏版本。表达式 `@with var=>val expr` 在一个新的动态作用域中评估 `expr`，其中 `var` 设置为 `val`。`val` 将被转换为类型 `T`。`@with var=>val expr` 等价于 `with(var=>val) do expr end`，但 `@with` 避免了创建闭包。

另请参见: [`ScopedValues.with`](@ref), [`ScopedValues.ScopedValue`](@ref), [`ScopedValues.get`](@ref)。

# 示例

```jldoctest
julia> using Base.ScopedValues

julia> const a = ScopedValue(1);

julia> f(x) = a[] + x;

julia> @with a=>2 f(10)
12

julia> @with a=>3 begin
           x = 100
           f(x)
       end
103
```
