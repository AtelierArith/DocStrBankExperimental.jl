```
invokelatest(f, args...; kwargs...)
```

调用 `f(args...; kwargs...)`，但保证将执行 `f` 的最新方法。这在某些特殊情况下非常有用，例如长时间运行的事件循环或可能调用过时版本的回调函数 `f`。（缺点是 `invokelatest` 的速度比直接调用 `f` 稍慢，并且结果的类型无法被编译器推断。）

!!! compat "Julia 1.9"
    在 Julia 1.9 之前，此函数未被导出，称为 `Base.invokelatest`。

