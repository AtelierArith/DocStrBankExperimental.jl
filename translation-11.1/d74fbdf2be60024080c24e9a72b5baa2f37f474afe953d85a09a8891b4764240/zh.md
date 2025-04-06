# SubArrays

Julia 的 `SubArray` 类型是一个容器，编码了父级 [`AbstractArray`](@ref) 的“视图”。 本页面记录了 `SubArray` 的一些设计原则和实现。

其中一个主要设计目标是确保 [`IndexLinear`](@ref) 和 [`IndexCartesian`](@ref) 数组的视图具有高性能。此外，`IndexLinear` 数组的视图应尽可能地保持为 `IndexLinear`。

## Index replacement

考虑对 3D 数组进行 2D 切片：

```@meta
DocTestSetup = :(import Random; Random.seed!(1234))
```

```jldoctest subarray
julia> A = rand(2,3,4);

julia> S1 = view(A, :, 1, 2:3)
2×2 view(::Array{Float64, 3}, :, 1, 2:3) with eltype Float64:
 0.839622  0.711389
 0.967143  0.103929

julia> S2 = view(A, 1, :, 2:3)
3×2 view(::Array{Float64, 3}, 1, :, 2:3) with eltype Float64:
 0.839622  0.711389
 0.789764  0.806704
 0.566704  0.962715
```

```@meta
DocTestSetup = nothing
```

`view` 会去掉“单例”维度（由 `Int` 指定的维度），因此 `S1` 和 `S2` 都是二维的 `SubArray`。因此，索引这些的自然方式是使用 `S1[i,j]`。要从父数组 `A` 中提取值，自然的方法是将 `S1[i,j]` 替换为 `A[i,1,(2:3)[j]]`，将 `S2[i,j]` 替换为 `A[1,i,(2:3)[j]]`。

SubArrays 设计的关键特性是，这种索引替换可以在没有任何运行时开销的情况下进行。

## SubArray design

### Type parameters and fields

所采用的策略首先体现在类型的定义中：

```julia
struct SubArray{T,N,P,I,L} <: AbstractArray{T,N}
    parent::P
    indices::I
    offset1::Int       # for linear indexing and pointer, only valid when L==true
    stride1::Int       # used only for linear indexing
    ...
end
```

`SubArray` 有 5 个类型参数。前两个是标准的元素类型和维度。下一个是父 `AbstractArray` 的类型。最常用的是第四个参数，它是一个 `Tuple`，包含每个维度的索引类型。最后一个参数 `L` 仅作为调度的便利提供；它是一个布尔值，表示索引类型是否支持快速线性索引。稍后会详细介绍。

如果在我们上面的例子中 `A` 是一个 `Array{Float64, 3}`，那么我们上面的 `S1` 情况将是一个 `SubArray{Float64,2,Array{Float64,3},Tuple{Base.Slice{Base.OneTo{Int64}},Int64,UnitRange{Int64}},false}`。特别注意元组参数，它存储了用于创建 `S1` 的索引类型。同样，

```jldoctest subarray
julia> S1.indices
(Base.Slice(Base.OneTo(2)), 1, 2:3)
```

存储这些值允许索引替换，并且将类型编码为参数使得可以调度到高效的算法。

### Index translation

执行索引转换需要对不同的具体 `SubArray` 类型做不同的处理。例如，对于 `S1`，需要将 `i,j` 索引应用于父数组的第一和第三维，而对于 `S2`，则需要将它们应用于第二和第三维。最简单的索引方法是在运行时进行类型分析：

```julia
parentindices = Vector{Any}()
for thisindex in S.indices
    ...
    if isa(thisindex, Int)
        # Don't consume one of the input indices
        push!(parentindices, thisindex)
    elseif isa(thisindex, AbstractVector)
        # Consume an input index
        push!(parentindices, thisindex[inputindex[j]])
        j += 1
    elseif isa(thisindex, AbstractMatrix)
        # Consume two input indices
        push!(parentindices, thisindex[inputindex[j], inputindex[j+1]])
        j += 2
    elseif ...
end
S.parent[parentindices...]
```

不幸的是，这在性能方面将是灾难性的：每次访问元素都会分配内存，并且涉及大量类型不佳的代码的运行。

更好的方法是调度到特定的方法来处理每种类型的存储索引。这就是 `reindex` 的作用：它根据第一个存储索引的类型进行调度，并消耗适当数量的输入索引，然后对剩余的索引进行递归。在 `S1` 的情况下，这扩展为

```julia
Base.reindex(S1, S1.indices, (i, j)) == (i, S1.indices[2], S1.indices[3][j])
```

对于任何一对索引 `(i,j)`（除了 [`CartesianIndex`](@ref) 及其数组，见下文）。

这是 `SubArray` 的核心；索引方法依赖于 `reindex` 来进行索引转换。不过，有时我们可以避免间接调用，从而使其更快。

### Linear indexing

线性索引可以高效地实现，当整个数组具有一个单一的步幅来分隔连续元素，从某个偏移量开始。这意味着我们可以预先计算这些值，并将线性索引简单地表示为加法和乘法，从而避免 `reindex` 的间接性（更重要的是）完全避免笛卡尔坐标的慢计算。

对于 `SubArray` 类型，高效线性索引的可用性完全基于索引的类型，而不依赖于父数组的大小等值。您可以使用内部的 `Base.viewindexing` 函数询问给定的索引集是否支持快速线性索引：

```jldoctest subarray
julia> Base.viewindexing(S1.indices)
IndexCartesian()

julia> Base.viewindexing(S2.indices)
IndexLinear()
```

这是在构造 `SubArray` 时计算的，并作为布尔值存储在 `L` 类型参数中，编码了快速线性索引支持。虽然不是严格必要，但这意味着我们可以直接在 `SubArray{T,N,A,I,true}` 上定义调度，而不需要任何中介。

由于此计算不依赖于运行时值，因此可能会遗漏一些步幅恰好是均匀的情况：

```jldoctest
julia> A = reshape(1:4*2, 4, 2)
4×2 reshape(::UnitRange{Int64}, 4, 2) with eltype Int64:
 1  5
 2  6
 3  7
 4  8

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 2
 2
```

一个视图构造为 `view(A, 2:2:4, :)` 恰好具有均匀步幅，因此线性索引确实可以高效地执行。然而，在这种情况下的成功取决于数组的大小：如果第一维是奇数，

```jldoctest
julia> A = reshape(1:5*2, 5, 2)
5×2 reshape(::UnitRange{Int64}, 5, 2) with eltype Int64:
 1   6
 2   7
 3   8
 4   9
 5  10

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 3
 2
```

然后 `A[2:2:4,:]` 没有统一的步幅，因此我们无法保证高效的线性索引。由于我们必须仅根据 `SubArray` 参数中编码的类型来做出这个决定，`S = view(A, 2:2:4, :)` 无法实现高效的线性索引。

### A few details

  * 请注意，`Base.reindex` 函数与输入索引的类型无关；它仅确定存储的索引应该如何以及在哪里重新索引。它不仅支持整数索引，还支持非标量索引。这意味着视图的视图不需要两个间接级别；它们可以简单地重新计算到原始父数组的索引！
  * 希望到现在为止，支持切片的含义已经相当清楚，即由参数 `N` 给出的维度不一定等于父数组的维度或 `indices` 元组的长度。用户提供的索引也不一定与 `indices` 元组中的条目对齐（例如，第二个用户提供的索引可能对应于父数组的第三维，而 `indices` 元组中的第三个元素）。

    不太明显的是，存储的父数组的维度必须等于`indices`元组中有效索引的数量。一些示例：

    ```julia
    A = reshape(1:35, 5, 7) # A 2d parent Array
    S = view(A, 2:7)         # A 1d view created by linear indexing
    S = view(A, :, :, 1:1)   # Appending extra indices is supported
    ```

    天真地，你可能会认为只需设置 `S.parent = A` 和 `S.indices = (:,:,1:1)`，但支持这一点会大大复杂化重新索引过程，尤其是对于视图的视图。不仅需要根据存储索引的类型进行调度，还需要检查给定索引是否是最后一个，并将任何剩余的存储索引“合并”在一起。这不是一项简单的任务，更糟糕的是：它很慢，因为它隐式依赖于线性索引。

    幸运的是，这正是 `ReshapedArray` 所执行的计算，并且如果可能的话，它是线性执行的。因此，`view` 确保父数组对于给定的索引具有适当的维度，如果需要的话会对其进行重塑。内部的 `SubArray` 构造函数确保满足这一不变性。
  * [`CartesianIndex`](@ref) 和数组的组合给 `reindex` 方案带来了麻烦。请记住，`reindex` 仅根据存储的索引类型来分派，以确定应该使用多少个传递的索引以及它们应该放在哪里。但是对于 `CartesianIndex`，传递的参数数量与它们所索引的维度数量之间不再是一一对应的。如果我们回到上面的例子 `Base.reindex(S1, S1.indices, (i, j))`，你会发现对于 `i, j = CartesianIndex(), CartesianIndex(2,1)`，扩展是不正确的。它应该*完全跳过* `CartesianIndex()` 并返回：

    ```julia
    (CartesianIndex(2,1)[1], S1.indices[2], S1.indices[3][CartesianIndex(2,1)[2]])
    ```

    相反，我们得到的是：

    ```julia
    (CartesianIndex(), S1.indices[2], S1.indices[3][CartesianIndex(2,1)])
    ```

    正确地做到这一点需要在所有维度组合中对存储和传递的索引进行*组合*调度，这在不可处理的情况下是不可行的。因此，`reindex` 绝不能与 `CartesianIndex` 索引一起调用。幸运的是，标量情况可以通过首先将 `CartesianIndex` 参数展平为普通整数来轻松处理。然而，`CartesianIndex` 的数组不能如此轻易地分割成正交部分。在尝试使用 `reindex` 之前，`view` 必须确保参数列表中没有 `CartesianIndex` 的数组。如果有，它可以简单地“放弃”，完全避免 `reindex` 计算，而是构造一个具有两个间接级别的嵌套 `SubArray`。
