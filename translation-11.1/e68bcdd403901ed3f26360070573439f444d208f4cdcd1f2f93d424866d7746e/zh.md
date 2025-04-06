```
complex(r, [i])
```

将实数或数组转换为复数。`i` 默认为零。

# 示例

```jldoctest
julia> complex(7)
7 + 0im

julia> complex([1, 2, 3])
3-element Vector{Complex{Int64}}:
 1 + 0im
 2 + 0im
 3 + 0im
```
