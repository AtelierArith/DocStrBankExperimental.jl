```
Channel{T=Any}(size::Int=0)
```

构造一个 `Channel`，其内部缓冲区最多可以容纳 `size` 个类型为 `T` 的对象。对满的通道调用 [`put!`](@ref) 会阻塞，直到通过 [`take!`](@ref) 移除一个对象。

`Channel(0)` 构造一个无缓冲通道。`put!` 会阻塞，直到调用匹配的 `take!`。反之亦然。

其他构造函数：

  * `Channel()`: 默认构造函数，相当于 `Channel{Any}(0)`
  * `Channel(Inf)`: 相当于 `Channel{Any}(typemax(Int))`
  * `Channel(sz)`: 相当于 `Channel{Any}(sz)`

!!! compat "Julia 1.3"
    默认构造函数 `Channel()` 和默认 `size=0` 是在 Julia 1.3 中添加的。

