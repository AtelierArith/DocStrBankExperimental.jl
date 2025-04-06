```
range(start, stop, length)
range(start, stop; length, step)
range(start; length, stop, step)
range(;start, length, stop, step)
```

从参数构造一个具有均匀间隔元素和优化存储的专用数组（一个 [`AbstractRange`](@ref)）。在数学上，范围是由 `start`、`step`、`stop` 和 `length` 中的任意三个唯一确定的。有效的范围调用包括：

  * 使用 `start`、`step`、`stop`、`length` 中的任意三个调用 `range`。
  * 使用 `start`、`stop`、`length` 中的两个调用 `range`。在这种情况下，`step` 将被假定为 1。如果两个参数都是整数，将返回一个 [`UnitRange`](@ref)。
  * 使用 `stop` 或 `length` 中的一个调用 `range`。`start` 和 `step` 将被假定为 1。

有关返回类型的更多详细信息，请参见扩展帮助。另请参见 [`logrange`](@ref) 以获取对数间隔点。

# 示例

```jldoctest
julia> range(1, length=100)
1:100

julia> range(1, stop=100)
1:100

julia> range(1, step=5, length=100)
1:5:496

julia> range(1, step=5, stop=100)
1:5:96

julia> range(1, 10, length=101)
1.0:0.09:10.0

julia> range(1, 100, step=5)
1:5:96

julia> range(stop=10, length=5)
6:10

julia> range(stop=10, step=1, length=5)
6:1:10

julia> range(start=1, step=1, stop=10)
1:1:10

julia> range(; length = 10)
Base.OneTo(10)

julia> range(; stop = 6)
Base.OneTo(6)

julia> range(; stop = 6.5)
1.0:1.0:6.0
```

如果未指定 `length` 且 `stop - start` 不是 `step` 的整数倍，则将生成一个在 `stop` 之前结束的范围。

```jldoctest
julia> range(1, 3.5, step=2)
1.0:2.0:3.0
```

特别注意确保中间值以有理数计算。要避免这种引入的开销，请参见 [`LinRange`](@ref) 构造函数。

!!! compat "Julia 1.1"
    `stop` 作为位置参数至少需要 Julia 1.1。


!!! compat "Julia 1.7"
    没有关键字参数且 `start` 作为关键字参数的版本至少需要 Julia 1.7。


!!! compat "Julia 1.8"
    仅将 `stop` 作为唯一关键字参数或仅将 `length` 作为唯一关键字参数的版本至少需要 Julia 1.8。


# 扩展帮助

当参数为整数且

  * 仅提供 `length`
  * 仅提供 `stop`

时，`range` 将生成一个 `Base.OneTo`。

当参数为整数且

  * 仅提供 `start` 和 `stop`
  * 仅提供 `length` 和 `stop`

时，`range` 将生成一个 `UnitRange`。

如果提供了 `step`，即使指定为 1，也不会生成 `UnitRange`。
