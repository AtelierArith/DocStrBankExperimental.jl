```
invoke(f, argtypes::Type, args...; kwargs...)
```

调用给定泛型函数 `f` 的方法，匹配指定类型 `argtypes` 和指定参数 `args`，并传递关键字参数 `kwargs`。参数 `args` 必须符合 `argtypes` 中指定的类型，即不自动执行转换。此方法允许调用与最特定匹配方法不同的方法，这在明确需要更一般定义的行为时非常有用（通常作为同一函数的更特定方法实现的一部分）。

在使用 `invoke` 调用你未编写的函数时要小心。对于给定的 `argtypes` 使用哪个定义是一个实现细节，除非该函数明确声明使用某些 `argtypes` 调用是公共 API 的一部分。例如，下面示例中 `f1` 和 `f2` 之间的变化通常被认为是兼容的，因为这种变化在正常（非 `invoke`）调用中对调用者是不可见的。然而，如果使用 `invoke`，这种变化是可见的。

# 示例

```jldoctest
julia> f(x::Real) = x^2;

julia> f(x::Integer) = 1 + invoke(f, Tuple{Real}, x);

julia> f(2)
5

julia> f1(::Integer) = Integer
       f1(::Real) = Real;

julia> f2(x::Real) = _f2(x)
       _f2(::Integer) = Integer
       _f2(_) = Real;

julia> f1(1)
Integer

julia> f2(1)
Integer

julia> invoke(f1, Tuple{Real}, 1)
Real

julia> invoke(f2, Tuple{Real}, 1)
Integer
```
