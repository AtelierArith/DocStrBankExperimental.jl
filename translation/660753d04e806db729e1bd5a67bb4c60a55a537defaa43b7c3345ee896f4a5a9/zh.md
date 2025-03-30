```
issetequal(x)
```

创建一个函数，该函数使用 [`issetequal`](@ref) 将其参数与 `x` 进行比较，即一个等价于 `y -> issetequal(y, x)` 的函数。返回的函数类型为 `Base.Fix2{typeof(issetequal)}`，可用于实现专门的方法。

!!! compat "Julia 1.11"
    此功能至少需要 Julia 1.11。

