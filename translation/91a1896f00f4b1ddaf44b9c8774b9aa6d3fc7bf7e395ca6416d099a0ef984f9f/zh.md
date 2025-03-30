```
@views 表达式
```

将给定表达式（可以是 `begin`/`end` 块、循环、函数等）中的每个数组切片操作转换为返回视图。标量索引、非数组类型和显式 [`getindex`](@ref) 调用（与 `array[...]` 相对）不受影响。

同样，`@views` 将字符串切片转换为 [`SubString`](@ref) 视图。

!!! 注意     `@views` 宏仅影响在给定 `expression` 中显式出现的 `array[...]` 表达式，而不影响由该代码调用的函数中发生的数组切片。

!!! 兼容 "Julia 1.5"     在索引表达式中使用 `begin` 来引用第一个索引是在 Julia 1.4 中实现的，但仅在 Julia 1.5 开始支持 `@views`。

# 示例

```jldoctest
julia> A = zeros(3, 3);

julia> @views for row in 1:3
           b = A[row, :] # b 是一个视图，而不是一个副本
           b .= row      # 将每个元素赋值为行索引
       end

julia> A
3×3 Matrix{Float64}:
 1.0  1.0  1.0
 2.0  2.0  2.0
 3.0  3.0  3.0
```
