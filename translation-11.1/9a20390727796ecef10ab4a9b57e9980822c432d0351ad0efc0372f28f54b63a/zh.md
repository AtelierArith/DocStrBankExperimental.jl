```
Random.default_rng() -> rng
```

返回默认的全局随机数生成器（RNG），当没有提供显式的RNG时，`rand`相关函数将使用它。

当加载`Random`模块时，默认的RNG会通过[`Random.seed!()`](@ref)进行*随机*初始化：这意味着每次启动新的julia会话时，第一次调用`rand()`会产生不同的结果，除非首先调用`seed!(seed)`。

它是线程安全的：不同的线程可以安全地并发调用`default_rng()`上的`rand`相关函数，例如`rand(default_rng())`。

!!! note
    默认RNG的类型是一个实现细节。在不同版本的Julia中，您不应期望默认RNG始终具有相同的类型，也不应期望它在给定种子时产生相同的随机数流。


!!! compat "Julia 1.3"
    此函数是在Julia 1.3中引入的。

