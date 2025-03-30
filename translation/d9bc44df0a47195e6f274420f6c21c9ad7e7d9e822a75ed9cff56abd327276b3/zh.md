```
-(x)
```

一元负号运算符。

另请参见：[`abs`](@ref), [`flipsign`](@ref)。

# 示例

```jldoctest
julia> -1
-1

julia> -(2)
-2

julia> -[1 2; 3 4]
2×2 矩阵{Int64}:
 -1  -2
 -3  -4

julia> -(true)  # 提升为 Int
-1

julia> -(0x003)
0xfffd
```
