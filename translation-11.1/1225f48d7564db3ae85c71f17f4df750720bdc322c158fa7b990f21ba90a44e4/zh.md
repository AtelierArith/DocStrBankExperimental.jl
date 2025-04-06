```
isequal(x)
```

创建一个函数，该函数使用 [`isequal`](@ref) 将其参数与 `x` 进行比较，即一个等价于 `y -> isequal(y, x)` 的函数。

返回的函数类型为 `Base.Fix2{typeof(isequal)}`，可用于实现专门的方法。
