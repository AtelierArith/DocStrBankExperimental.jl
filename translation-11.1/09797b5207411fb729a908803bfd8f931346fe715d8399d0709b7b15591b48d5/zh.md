```
stack(f, args...; [dims])
```

对集合的每个元素应用一个函数，并将结果进行 `stack`。或者对几个集合进行 [`zip`](@ref) 操作。

该函数应返回大小相同的数组（或元组，或其他迭代器）。这些将成为结果的切片，每个切片沿着 `dims`（如果给定）或默认沿着最后的维度分隔。

另请参见 [`mapslices`](@ref)，[`eachcol`](@ref)。

# 示例

```jldoctest
julia> stack(c -> (c, c-32), "julia")
2×5 Matrix{Char}:
 'j'  'u'  'l'  'i'  'a'
 'J'  'U'  'L'  'I'  'A'

julia> stack(eachrow([1 2 3; 4 5 6]), (10, 100); dims=1) do row, n
         vcat(row, row .* n, row ./ n)
       end
2×9 Matrix{Float64}:
 1.0  2.0  3.0   10.0   20.0   30.0  0.1   0.2   0.3
 4.0  5.0  6.0  400.0  500.0  600.0  0.04  0.05  0.06
```
