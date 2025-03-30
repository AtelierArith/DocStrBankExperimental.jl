```
AbstractIrrational <: Real
```

表示精确无理值的数字类型，在与其他数值进行算术运算时会自动四舍五入到正确的精度。

子类型 `MyIrrational <: AbstractIrrational` 应至少实现 `==(::MyIrrational, ::MyIrrational)`、`hash(x::MyIrrational, h::UInt)` 和 `convert(::Type{F}, x::MyIrrational) where {F <: Union{BigFloat,Float32,Float64}}`。

如果子类型用于表示可能偶尔为有理数的值（例如，表示 `√n` 的平方根类型，当整数 `n` 为完全平方时将给出有理结果），则还应实现 `isinteger`、`iszero`、`isone` 和与 `Real` 值的 `==`（因为所有这些在 `AbstractIrrational` 类型中默认返回 `false`），并且定义 [`hash`](@ref) 使其等于相应的 `Rational` 的哈希值。
