```
circcopy!(dest, src)
```

将 `src` 复制到 `dest`，对每个维度的索引进行模其长度的操作。`src` 和 `dest` 必须具有相同的大小，但可以在其索引中有偏移；任何偏移都会导致（循环）包裹。如果数组具有重叠的索引，则在重叠的域上，`dest` 与 `src` 一致。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


另请参见: [`circshift`](@ref).

# 示例

```julia-repl
julia> src = reshape(Vector(1:16), (4,4))
4×4 Array{Int64,2}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> dest = OffsetArray{Int}(undef, (0:3,2:5))

julia> circcopy!(dest, src)
OffsetArrays.OffsetArray{Int64,2,Array{Int64,2}} with indices 0:3×2:5:
 8  12  16  4
 5   9  13  1
 6  10  14  2
 7  11  15  3

julia> dest[1:3,2:4] == src[1:3,2:4]
true
```
