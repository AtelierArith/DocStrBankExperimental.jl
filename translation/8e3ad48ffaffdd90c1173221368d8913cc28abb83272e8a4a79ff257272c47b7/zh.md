```
similar(array, [element_type=eltype(array)], [dims=size(array)])
```

创建一个未初始化的可变数组，其元素类型和大小基于给定的源数组。第二个和第三个参数都是可选的，默认为给定数组的 `eltype` 和 `size`。维度可以作为单个元组参数或一系列整数参数来指定。

自定义的 AbstractArray 子类型可以选择哪种特定的数组类型最适合返回给定的元素类型和维度。如果它们不专门化此方法，默认返回的是 `Array{element_type}(undef, dims...)`。

例如，`similar(1:10, 1, 4)` 返回一个未初始化的 `Array{Int,2}`，因为范围既不可变也不支持 2 维：

```julia-repl
julia> similar(1:10, 1, 4)
1×4 Matrix{Int64}:
 4419743872  4374413872  4419743888  0
```

相反，`similar(trues(10,10), 2)` 返回一个未初始化的 `BitVector`，其中有两个元素，因为 `BitArray` 既可变又可以支持 1 维数组：

```julia-repl
julia> similar(trues(10,10), 2)
2-element BitVector:
 0
 0
```

然而，由于 `BitArray` 只能存储 [`Bool`](@ref) 类型的元素，如果请求不同的元素类型，它将创建一个常规的 `Array`：

```julia-repl
julia> similar(falses(10), Float64, 2, 4)
2×4 Matrix{Float64}:
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
```

另请参见: [`undef`](@ref), [`isassigned`](@ref).
