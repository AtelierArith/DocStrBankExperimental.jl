```
CachingPool(workers::Vector{Int})
```

`AbstractWorkerPool` 的实现。 [`remote`](@ref), [`remotecall_fetch`](@ref), [`pmap`](@ref)（以及其他远程调用，这些调用远程执行函数）受益于在工作节点上缓存序列化/反序列化的函数，特别是闭包（可能捕获大量数据）。

远程缓存在返回的 `CachingPool` 对象的生命周期内维护。要提前清除缓存，请使用 `clear!(pool)`。

对于全局变量，仅在闭包中捕获绑定，而不是数据。可以使用 `let` 块来捕获全局数据。

# 示例

```julia
const foo = rand(10^8);
wp = CachingPool(workers())
let foo = foo
    pmap(i -> sum(foo) + i, wp, 1:100);
end
```

上述代码只会将 `foo` 转移到每个工作节点一次。
