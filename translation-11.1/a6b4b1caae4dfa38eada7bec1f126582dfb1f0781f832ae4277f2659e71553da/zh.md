# [Arrays](@id lib-arrays)

## Constructors and Types

```@docs
Core.AbstractArray
Base.AbstractVector
Base.AbstractMatrix
Base.AbstractVecOrMat
Core.Array
Core.Array(::UndefInitializer, ::Any)
Core.Array(::Nothing, ::Any)
Core.Array(::Missing, ::Any)
Core.UndefInitializer
Core.undef
Base.Vector
Base.Vector(::UndefInitializer, ::Any)
Base.Vector(::Nothing, ::Any)
Base.Vector(::Missing, ::Any)
Base.Matrix
Base.Matrix(::UndefInitializer, ::Any, ::Any)
Base.Matrix(::Nothing, ::Any, ::Any)
Base.Matrix(::Missing, ::Any, ::Any)
Base.VecOrMat
Core.DenseArray
Base.DenseVector
Base.DenseMatrix
Base.DenseVecOrMat
Base.StridedArray
Base.StridedVector
Base.StridedMatrix
Base.StridedVecOrMat
Base.GenericMemory
Base.Memory
Base.memoryref
Base.Slices
Base.RowSlices
Base.ColumnSlices
Base.getindex(::Type, ::Any...)
Base.zeros
Base.ones
Base.BitArray
Base.BitArray(::UndefInitializer, ::Integer...)
Base.BitArray(::Any)
Base.trues
Base.falses
Base.fill
Base.fill!
Base.empty
Base.similar
```

## Basic functions

```@docs
Base.ndims
Base.size
Base.axes(::Any)
Base.axes(::AbstractArray, ::Any)
Base.length(::AbstractArray)
Base.keys(::AbstractArray)
Base.eachindex
Base.IndexStyle
Base.IndexLinear
Base.IndexCartesian
Base.conj!
Base.stride
Base.strides
```

## Broadcast and vectorization

另请参见 [dot syntax for vectorizing functions](@ref man-vectorized)；例如，`f.(args...)` 隐式调用 `broadcast(f, args...)`。与其依赖于 `sin` 等函数的“向量化”方法来处理数组，不如使用 `sin.(a)` 通过 `broadcast` 进行向量化。

```@docs
Base.broadcast
Base.Broadcast.broadcast!
Base.@__dot__
```

有关自定义类型的专门广播，请参见

```@docs
Base.BroadcastStyle
Base.Broadcast.AbstractArrayStyle
Base.Broadcast.ArrayStyle
Base.Broadcast.DefaultArrayStyle
Base.Broadcast.broadcastable
Base.Broadcast.combine_axes
Base.Broadcast.combine_styles
Base.Broadcast.result_style
```

## Indexing and assignment

```@docs
Base.getindex(::AbstractArray, ::Any...)
Base.setindex!(::AbstractArray, ::Any, ::Any...)
Base.nextind
Base.prevind
Base.copyto!(::AbstractArray, ::CartesianIndices, ::AbstractArray, ::CartesianIndices)
Base.copy!
Base.isassigned
Base.Colon
Base.CartesianIndex
Base.CartesianIndices
Base.Dims
Base.LinearIndices
Base.to_indices
Base.checkbounds
Base.checkindex
Base.elsize
```

## Views (SubArrays and other view types)

“视图”是一种数据结构，类似于数组（它是 `AbstractArray` 的一个子类型），但其底层数据实际上是另一个数组的一部分。

例如，如果 `x` 是一个数组，且 `v = @view x[1:10]`，那么 `v` 的行为就像一个包含 10 个元素的数组，但它的数据实际上是访问 `x` 的前 10 个元素。对视图进行写入，例如 `v[3] = 2`，会直接写入底层数组 `x`（在这种情况下修改 `x[3]`）。

切片操作如 `x[1:10]` 默认会在 Julia 中创建一个副本。`@view x[1:10]` 将其更改为使用视图。`@views` 宏可以用于整个代码块（例如 `@views function foo() .... end` 或 `@views begin ... end`），以将该块中的所有切片操作更改为使用视图。有时创建数据的副本更快，有时使用视图更快，正如在 [performance tips](@ref man-performance-views) 中所描述的。

```@docs
Base.view
Base.@view
Base.@views
Base.parent
Base.parentindices
Base.selectdim
Base.reinterpret
Base.reshape
Base.dropdims
Base.vec
Base.SubArray
```

## Concatenation and permutation

```@docs
Base.cat
Base.vcat
Base.hcat
Base.hvcat
Base.hvncat
Base.stack
Base.vect
Base.circshift
Base.circshift!
Base.circcopy!
Base.findall(::Any)
Base.findall(::Function, ::Any)
Base.findfirst(::Any)
Base.findfirst(::Function, ::Any)
Base.findlast(::Any)
Base.findlast(::Function, ::Any)
Base.findnext(::Any, ::Integer)
Base.findnext(::Function, ::Any, ::Integer)
Base.findprev(::Any, ::Integer)
Base.findprev(::Function, ::Any, ::Integer)
Base.permutedims
Base.permutedims!
Base.PermutedDimsArray
Base.promote_shape
```

## Array functions

```@docs
Base.accumulate
Base.accumulate!
Base.cumprod
Base.cumprod!
Base.cumsum
Base.cumsum!
Base.diff
Base.repeat
Base.rot180
Base.rotl90
Base.rotr90
Base.mapslices
Base.eachrow
Base.eachcol
Base.eachslice
```

## Combinatorics

```@docs
Base.invperm
Base.isperm
Base.permute!(::Any, ::AbstractVector)
Base.invpermute!
Base.reverse(::AbstractVector; kwargs...)
Base.reverseind
Base.reverse!
```
