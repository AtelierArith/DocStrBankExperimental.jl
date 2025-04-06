```
imag(A::AbstractArray)
```

返回一个数组，包含数组 `A` 中每个条目的虚部。

等价于 `imag.(A)`，但当 `A` 具有零维时，返回一个0维数组（而不是标量）。

# 示例

```jldoctest
julia> imag([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 0
 2
 4

julia> imag(fill(2 - im))
0-dimensional Array{Int64, 0}:
-1
```
