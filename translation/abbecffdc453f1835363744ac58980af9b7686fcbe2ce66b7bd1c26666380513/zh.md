# Interfaces

Julia 的强大和可扩展性来自于一系列非正式接口。通过扩展一些特定的方法以适用于自定义类型，该类型的对象不仅获得了这些功能，还能够在其他以通用方式构建这些行为的方法中使用。

## [Iteration](@id man-interface-iteration)

有两种方法是始终必需的：

| Required method         | Brief description                                                                        |
|:----------------------- |:---------------------------------------------------------------------------------------- |
| [`iterate(iter)`](@ref) | Returns either a tuple of the first item and initial state or [`nothing`](@ref) if empty |
| `iterate(iter, state)`  | Returns either a tuple of the next item and next state or `nothing` if no items remain   |

在某些情况下，还应该定义几种其他方法。请注意，您应该始终定义至少一个 `Base.IteratorSize(IterType)` 和 `length(iter)`，因为 `Base.IteratorSize(IterType)` 的默认定义是 `Base.HasLength()`。

| Method                                  | When should this method be defined?                                         | Default definition | Brief description                                                                                                                                                                                        |
|:--------------------------------------- |:--------------------------------------------------------------------------- |:------------------ |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Base.IteratorSize(IterType)`](@ref)   | If default is not appropriate                                               | `Base.HasLength()` | One of `Base.HasLength()`, `Base.HasShape{N}()`, `Base.IsInfinite()`, or `Base.SizeUnknown()` as appropriate                                                                                             |
| [`length(iter)`](@ref)                  | If `Base.IteratorSize()` returns `Base.HasLength()` or `Base.HasShape{N}()` | (*undefined*)      | The number of items, if known                                                                                                                                                                            |
| [`size(iter, [dim])`](@ref)             | If `Base.IteratorSize()` returns `Base.HasShape{N}()`                       | (*undefined*)      | The number of items in each dimension, if known                                                                                                                                                          |
| [`Base.IteratorEltype(IterType)`](@ref) | If default is not appropriate                                               | `Base.HasEltype()` | Either `Base.EltypeUnknown()` or `Base.HasEltype()` as appropriate                                                                                                                                       |
| [`eltype(IterType)`](@ref)              | If default is not appropriate                                               | `Any`              | The type of the first entry of the tuple returned by `iterate()`                                                                                                                                         |
| [`Base.isdone(iter, [state])`](@ref)    | **Must** be defined if iterator is stateful                                 | `missing`          | Fast-path hint for iterator completion. If not defined for a stateful iterator then functions that check for done-ness, like `isempty()` and `zip()`, may mutate the iterator and cause buggy behaviour! |

顺序迭代是通过 [`iterate`](@ref) 函数实现的。Julia 迭代器在迭代对象时不会改变对象，而是可以在对象外部跟踪迭代状态。`iterate` 的返回值始终是一个值和状态的元组，或者如果没有剩余元素则返回 `nothing`。状态对象将在下一次迭代时传回 `iterate` 函数，并通常被认为是与可迭代对象私有的实现细节。

任何定义此函数的对象都是可迭代的，可以在 [many functions that rely upon iteration](@ref lib-collections-iteration) 中使用。它也可以直接在 [`for`](@ref) 循环中使用，因为语法：

```julia
for item in iter   # or  "for item = iter"
    # body
end
```

请提供您希望翻译的Markdown内容或文本。

```julia
next = iterate(iter)
while next !== nothing
    (item, state) = next
    # body
    next = iterate(iter, state)
end
```

一个简单的例子是一个具有定义长度的平方数可迭代序列：

```jldoctest squaretype
julia> struct Squares
           count::Int
       end

julia> Base.iterate(S::Squares, state=1) = state > S.count ? nothing : (state*state, state+1)
```

仅凭 [`iterate`](@ref) 的定义，`Squares` 类型已经相当强大。我们可以遍历所有元素：

```jldoctest squaretype
julia> for item in Squares(7)
           println(item)
       end
1
4
9
16
25
36
49
```

我们可以使用许多与可迭代对象一起使用的内置方法，例如 [`in`](@ref) 或 [`sum`](@ref)：

```jldoctest squaretype
julia> 25 in Squares(10)
true

julia> sum(Squares(100))
338350
```

我们可以扩展一些方法，以便为 Julia 提供有关这个可迭代集合的更多信息。我们知道 `Squares` 序列中的元素将始终是 `Int`。通过扩展 [`eltype`](@ref) 方法，我们可以将该信息提供给 Julia，并帮助它在更复杂的方法中生成更专业化的代码。我们还知道序列中的元素数量，因此我们也可以扩展 [`length`](@ref)：

```jldoctest squaretype
julia> Base.eltype(::Type{Squares}) = Int # Note that this is defined for the type

julia> Base.length(S::Squares) = S.count
```

Now, when we ask Julia to [`collect`](@ref) all the elements into an array it can preallocate a `Vector{Int}` of the right size instead of naively [`push!`](@ref)ing each element into a `Vector{Any}`:

```jldoctest squaretype
julia> collect(Squares(4))
4-element Vector{Int64}:
  1
  4
  9
 16
```

虽然我们可以依赖通用实现，但我们也可以扩展特定方法，在我们知道有更简单的算法时。例如，有一个计算平方和的公式，因此我们可以用更高效的解决方案覆盖通用的迭代版本：

```jldoctest squaretype
julia> Base.sum(S::Squares) = (n = S.count; return n*(n+1)*(2n+1)÷6)

julia> sum(Squares(1803))
1955361914
```

这是在 Julia Base 中非常常见的模式：一小组必需的方法定义了一个非正式接口，使得许多更复杂的行为成为可能。在某些情况下，类型会希望在知道可以在其特定情况下使用更高效的算法时，额外专门化这些额外的行为。

它通常也很有用，可以通过反向迭代 [`Iterators.reverse(iterator)`](@ref) 来允许对集合进行*反向迭代*。然而，要实际支持反向迭代，迭代器类型 `T` 需要为 `Iterators.Reverse{T}` 实现 `iterate`。 （给定 `r::Iterators.Reverse{T}`，类型 `T` 的底层迭代器是 `r.itr`。）在我们的 `Squares` 示例中，我们将实现 `Iterators.Reverse{Squares}` 方法：

```jldoctest squaretype
julia> Base.iterate(rS::Iterators.Reverse{Squares}, state=rS.itr.count) = state < 1 ? nothing : (state*state, state-1)

julia> collect(Iterators.reverse(Squares(4)))
4-element Vector{Int64}:
 16
  9
  4
  1
```

## Indexing

| Methods to implement | Brief description                                             |
|:-------------------- |:------------------------------------------------------------- |
| `getindex(X, i)`     | `X[i]`, indexed access, non-scalar `i` should allocate a copy |
| `setindex!(X, v, i)` | `X[i] = v`, indexed assignment                                |
| `firstindex(X)`      | The first index, used in `X[begin]`                           |
| `lastindex(X)`       | The last index, used in `X[end]`                              |

对于上面的 `Squares` 可迭代对象，我们可以通过平方来轻松计算序列的第 `i` 个元素。我们可以将其作为索引表达式 `S[i]` 来暴露。要启用此行为，`Squares` 只需定义 [`getindex`](@ref)：

```jldoctest squaretype
julia> function Base.getindex(S::Squares, i::Int)
           1 <= i <= S.count || throw(BoundsError(S, i))
           return i*i
       end

julia> Squares(100)[23]
529
```

此外，为了支持语法 `S[begin]` 和 `S[end]`，我们必须定义 [`firstindex`](@ref) 和 [`lastindex`](@ref) 来分别指定第一个和最后一个有效索引：

```jldoctest squaretype
julia> Base.firstindex(S::Squares) = 1

julia> Base.lastindex(S::Squares) = length(S)

julia> Squares(23)[end]
529
```

对于多维的 `begin`/`end` 索引，例如 `a[3, begin, 7]`，你应该定义 `firstindex(a, dim)` 和 `lastindex(a, dim)`（默认调用 `axes(a, dim)` 的 `first` 和 `last`）。

请注意，上述内容*仅*定义了 [`getindex`](@ref)，并且只有一个整数索引。使用除 `Int` 以外的任何内容进行索引将抛出 [`MethodError`](@ref)，表示没有匹配的方法。为了支持使用范围或 `Int` 向量进行索引，必须编写单独的方法：

```jldoctest squaretype
julia> Base.getindex(S::Squares, i::Number) = S[convert(Int, i)]

julia> Base.getindex(S::Squares, I) = [S[i] for i in I]

julia> Squares(10)[[3,4.,5]]
3-element Vector{Int64}:
  9
 16
 25
```

虽然这开始支持更多的 [indexing operations supported by some of the builtin types](@ref man-array-indexing)，但仍然缺少相当多的行为。这个 `Squares` 序列开始看起来越来越像一个向量，因为我们为它添加了行为。我们可以正式将其定义为 [`AbstractArray`](@ref) 的一个子类型，而不是自己定义所有这些行为。

## [Abstract Arrays](@id man-interface-array)

| Methods to implement                     |                                        | Brief description                                                                                                                                                |
|:---------------------------------------- |:-------------------------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `size(A)`                                |                                        | Returns a tuple containing the dimensions of `A`                                                                                                                 |
| `getindex(A, i::Int)`                    |                                        | (if `IndexLinear`) Linear scalar indexing                                                                                                                        |
| `getindex(A, I::Vararg{Int, N})`         |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexing                                                                                        |
| **Optional methods**                     | **Default definition**                 | **Brief description**                                                                                                                                            |
| `IndexStyle(::Type)`                     | `IndexCartesian()`                     | Returns either `IndexLinear()` or `IndexCartesian()`. See the description below.                                                                                 |
| `setindex!(A, v, i::Int)`                |                                        | (if `IndexLinear`) Scalar indexed assignment                                                                                                                     |
| `setindex!(A, v, I::Vararg{Int, N})`     |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexed assignment                                                                              |
| `getindex(A, I...)`                      | defined in terms of scalar `getindex`  | [Multidimensional and nonscalar indexing](@ref man-array-indexing)                                                                                               |
| `setindex!(A, X, I...)`                  | defined in terms of scalar `setindex!` | [Multidimensional and nonscalar indexed assignment](@ref man-array-indexing)                                                                                     |
| `iterate`                                | defined in terms of scalar `getindex`  | Iteration                                                                                                                                                        |
| `length(A)`                              | `prod(size(A))`                        | Number of elements                                                                                                                                               |
| `similar(A)`                             | `similar(A, eltype(A), size(A))`       | Return a mutable array with the same shape and element type                                                                                                      |
| `similar(A, ::Type{S})`                  | `similar(A, S, size(A))`               | Return a mutable array with the same shape and the specified element type                                                                                        |
| `similar(A, dims::Dims)`                 | `similar(A, eltype(A), dims)`          | Return a mutable array with the same element type and size *dims*                                                                                                |
| `similar(A, ::Type{S}, dims::Dims)`      | `Array{S}(undef, dims)`                | Return a mutable array with the specified element type and size                                                                                                  |
| **Non-traditional indices**              | **Default definition**                 | **Brief description**                                                                                                                                            |
| `axes(A)`                                | `map(OneTo, size(A))`                  | Return a tuple of `AbstractUnitRange{<:Integer}` of valid indices. The axes should be their own axes, that is `axes.(axes(A),1) == axes(A)` should be satisfied. |
| `similar(A, ::Type{S}, inds)`            | `similar(A, S, Base.to_shape(inds))`   | Return a mutable array with the specified indices `inds` (see below)                                                                                             |
| `similar(T::Union{Type,Function}, inds)` | `T(Base.to_shape(inds))`               | Return an array similar to `T` with the specified indices `inds` (see below)                                                                                     |

如果一个类型被定义为 `AbstractArray` 的子类型，它继承了一套非常丰富的行为，包括基于单元素访问构建的迭代和多维索引。请参见 [arrays manual page](@ref man-multi-dim-arrays) 和 [Julia Base section](@ref lib-arrays) 以获取更多支持的方法。

定义 `AbstractArray` 子类型的一个关键部分是 [`IndexStyle`](@ref)。由于索引是数组中一个重要的部分，并且通常出现在热循环中，因此使索引和索引赋值尽可能高效是很重要的。数组数据结构通常以两种方式之一定义：要么它最有效地使用一个索引（线性索引）访问其元素，要么它本质上使用为每个维度指定的索引访问元素。这两种模式在 Julia 中被识别为 `IndexLinear()` 和 `IndexCartesian()`。将线性索引转换为多个索引下标通常是非常昂贵的，因此这提供了一种基于特征的机制，以便为所有数组类型启用高效的通用代码。

这种区分决定了类型必须定义哪些标量索引方法。`IndexLinear()` 数组很简单：只需定义 `getindex(A::ArrayType, i::Int)`。当数组随后使用多维索引集进行索引时，后备的 `getindex(A::AbstractArray, I...)` 会高效地将索引转换为一个线性索引，然后调用上述方法。另一方面，`IndexCartesian()` 数组要求为每个支持的维度定义方法，使用 `ndims(A)` 的 `Int` 索引。例如，来自 `SparseArrays` 标准库模块的 [`SparseMatrixCSC`](@ref) 仅支持两个维度，因此它只定义了 `getindex(A::SparseMatrixCSC, i::Int, j::Int)`。对于 [`setindex!`](@ref) 也是如此。

返回到上面的平方序列，我们可以将其定义为 `AbstractArray{Int, 1}` 的一个子类型：

```jldoctest squarevectype
julia> struct SquaresVector <: AbstractArray{Int, 1}
           count::Int
       end

julia> Base.size(S::SquaresVector) = (S.count,)

julia> Base.IndexStyle(::Type{<:SquaresVector}) = IndexLinear()

julia> Base.getindex(S::SquaresVector, i::Int) = i*i
```

请注意，指定 `AbstractArray` 的两个参数非常重要；第一个定义 [`eltype`](@ref)，第二个定义 [`ndims`](@ref)。这个超类型和这三个方法使得 `SquaresVector` 成为一个可迭代、可索引且完全功能的数组：

```jldoctest squarevectype
julia> s = SquaresVector(4)
4-element SquaresVector:
  1
  4
  9
 16

julia> s[s .> 8]
2-element Vector{Int64}:
  9
 16

julia> s + s
4-element Vector{Int64}:
  2
  8
 18
 32

julia> sin.(s)
4-element Vector{Float64}:
  0.8414709848078965
 -0.7568024953079282
  0.4121184852417566
 -0.2879033166650653
```

作为一个更复杂的例子，让我们定义我们自己的玩具 N 维稀疏数组类型，基于 [`Dict`](@ref)：

```jldoctest squarevectype
julia> struct SparseArray{T,N} <: AbstractArray{T,N}
           data::Dict{NTuple{N,Int}, T}
           dims::NTuple{N,Int}
       end

julia> SparseArray(::Type{T}, dims::Int...) where {T} = SparseArray(T, dims);

julia> SparseArray(::Type{T}, dims::NTuple{N,Int}) where {T,N} = SparseArray{T,N}(Dict{NTuple{N,Int}, T}(), dims);

julia> Base.size(A::SparseArray) = A.dims

julia> Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where {T} = SparseArray(T, dims)

julia> Base.getindex(A::SparseArray{T,N}, I::Vararg{Int,N}) where {T,N} = get(A.data, I, zero(T))

julia> Base.setindex!(A::SparseArray{T,N}, v, I::Vararg{Int,N}) where {T,N} = (A.data[I] = v)
```

注意这是一个 `IndexCartesian` 数组，因此我们必须手动定义 [`getindex`](@ref) 和 [`setindex!`](@ref)，以适应数组的维度。与 `SquaresVector` 不同，我们能够定义 `4d61726b646f776e2e436f64652822222c2022736574696e646578212229_40726566`，因此我们可以改变数组：

```jldoctest squarevectype
julia> A = SparseArray(Float64, 3, 3)
3×3 SparseArray{Float64, 2}:
 0.0  0.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> fill!(A, 2)
3×3 SparseArray{Float64, 2}:
 2.0  2.0  2.0
 2.0  2.0  2.0
 2.0  2.0  2.0

julia> A[:] = 1:length(A); A
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

The result of indexing an `AbstractArray` can itself be an array (for instance when indexing by an `AbstractRange`). The `AbstractArray` fallback methods use [`similar`](@ref) to allocate an `Array` of the appropriate size and element type, which is filled in using the basic indexing method described above. However, when implementing an array wrapper you often want the result to be wrapped as well:

```jldoctest squarevectype
julia> A[1:2,:]
2×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
```

在这个例子中，通过定义 `Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where T` 来创建适当的包装数组。（请注意，虽然 `similar` 支持 1 和 2 个参数的形式，但在大多数情况下，您只需要专门化 3 个参数的形式。）为了使其工作，重要的是 `SparseArray` 是可变的（支持 `setindex!`）。为 `SparseArray` 定义 `similar`、`getindex` 和 `setindex!` 也使得可以 [`copy`](@ref) 数组：

```jldoctest squarevectype
julia> copy(A)
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

除了上述所有可迭代和可索引的方法，这些类型还可以相互交互，并使用 Julia Base 为 `AbstractArrays` 定义的大多数方法：

```jldoctest squarevectype
julia> A[SquaresVector(3)]
3-element SparseArray{Float64, 1}:
 1.0
 4.0
 9.0

julia> sum(A)
45.0
```

如果您正在定义一个允许非传统索引（索引从1以外的其他值开始）的数组类型，您应该专门化 [`axes`](@ref)。您还应该专门化 [`similar`](@ref)，以便 `dims` 参数（通常是一个 `Dims` 大小元组）可以接受 `AbstractUnitRange` 对象，也许是您自己设计的范围类型 `Ind`。有关更多信息，请参见 [Arrays with custom indices](@ref man-custom-indices)。

## [Strided Arrays](@id man-interface-strided-arrays)

| Methods to implement                     |                        | Brief description                                                                                                                                                                   |
|:---------------------------------------- |:---------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `strides(A)`                             |                        | Return the distance in memory (in number of elements) between adjacent elements in each dimension as a tuple. If `A` is an `AbstractArray{T,0}`, this should return an empty tuple. |
| `Base.unsafe_convert(::Type{Ptr{T}}, A)` |                        | Return the native address of an array.                                                                                                                                              |
| `Base.elsize(::Type{<:A})`               |                        | Return the stride between consecutive elements in the array.                                                                                                                        |
| **Optional methods**                     | **Default definition** | **Brief description**                                                                                                                                                               |
| `stride(A, i::Int)`                      | `strides(A)[i]`        | Return the distance in memory (in number of elements) between adjacent elements in dimension k.                                                                                     |

一个跨步数组是 `AbstractArray` 的一个子类型，其条目以固定的跨步存储在内存中。只要数组的元素类型与 BLAS 兼容，跨步数组就可以利用 BLAS 和 LAPACK 例程来实现更高效的线性代数例程。一个用户定义的跨步数组的典型示例是一个包装了标准 `Array` 的附加结构。

警告：如果底层存储实际上不是分步的，请不要实现这些方法，因为这可能导致不正确的结果或段错误。

以下是一些示例，以演示哪些类型的数组是跨步的，哪些不是：

```julia
1:5   # not strided (there is no storage associated with this array.)
Vector(1:5)  # is strided with strides (1,)
A = [1 5; 2 6; 3 7; 4 8]  # is strided with strides (1,4)
V = view(A, 1:2, :)   # is strided with strides (1,4)
V = view(A, 1:2:3, 1:2)   # is strided with strides (2,4)
V = view(A, [1,2,4], :)   # is not strided, as the spacing between rows is not fixed.
```

## [Customizing broadcasting](@id man-interfaces-broadcasting)

| Methods to implement                                       | Brief description                                                  |
|:---------------------------------------------------------- |:------------------------------------------------------------------ |
| `Base.BroadcastStyle(::Type{SrcType}) = SrcStyle()`        | Broadcasting behavior of `SrcType`                                 |
| `Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})` | Allocation of output container                                     |
| **Optional methods**                                       |                                                                    |
| `Base.BroadcastStyle(::Style1, ::Style2) = Style12()`      | Precedence rules for mixing styles                                 |
| `Base.axes(x)`                                             | Declaration of the indices of `x`, as per [`axes(x)`](@ref).       |
| `Base.broadcastable(x)`                                    | Convert `x` to an object that has `axes` and supports indexing     |
| **Bypassing default machinery**                            |                                                                    |
| `Base.copy(bc::Broadcasted{DestStyle})`                    | Custom implementation of `broadcast`                               |
| `Base.copyto!(dest, bc::Broadcasted{DestStyle})`           | Custom implementation of `broadcast!`, specializing on `DestStyle` |
| `Base.copyto!(dest::DestType, bc::Broadcasted{Nothing})`   | Custom implementation of `broadcast!`, specializing on `DestType`  |
| `Base.Broadcast.broadcasted(f, args...)`                   | Override the default lazy behavior within a fused expression       |
| `Base.Broadcast.instantiate(bc::Broadcasted{DestStyle})`   | Override the computation of the lazy broadcast's axes              |

[Broadcasting](@ref) 是通过显式调用 `broadcast` 或 `broadcast!` 触发的，或者通过像 `A .+ b` 或 `f.(x, y)` 这样的“点”操作隐式触发。任何具有 [`axes`](@ref) 并支持索引的对象都可以作为广播中的参数，默认情况下结果存储在 `Array` 中。这个基本框架可以通过三种主要方式进行扩展：

  * 确保所有参数支持广播
  * 为给定参数集选择合适的输出数组
  * 为给定参数集选择高效的实现

并不是所有类型都支持 `axes` 和索引，但许多类型在广播中允许使用是很方便的。[`Base.broadcastable`](@ref) 函数在每个参数上调用以进行广播，允许它返回支持 `axes` 和索引的不同内容。默认情况下，对于所有 `AbstractArray` 和 `Number`，这是恒等函数——它们已经支持 `axes` 和索引。

如果一个类型旨在像“0维标量”（单个对象）一样工作，而不是作为广播的容器，则应定义以下方法：

```julia
Base.broadcastable(o::MyType) = Ref(o)
```

该方法将参数包装在一个 0 维的 [`Ref`](@ref) 容器中。例如，这样的包装方法为类型本身、函数、特殊单例如 [`missing`](@ref) 和 [`nothing`](@ref) 以及日期定义。

自定义类数组类型可以专门化 `Base.broadcastable` 来定义它们的形状，但它们应该遵循这样的约定：`collect(Base.broadcastable(x)) == collect(x)`。一个显著的例外是 `AbstractString`；字符串被特殊处理，以便在广播时表现得像标量，尽管它们是其字符的可迭代集合（有关更多信息，请参见 [Strings](@ref)）。

接下来的两个步骤（选择输出数组和实现）依赖于为给定参数集确定一个单一答案。广播必须将其参数的所有不同类型压缩为一个输出数组和一个实现。广播将这个单一答案称为“样式”。每个可广播对象都有其自己首选的样式，并使用类似提升的系统将这些样式组合成一个单一答案——“目标样式”。

### Broadcast Styles

`Base.BroadcastStyle` 是所有广播样式派生的抽象类型。当作为函数使用时，它有两种可能的形式，单元（单参数）和双元。单元变体表示您打算实现特定的广播行为和/或输出类型，并且不希望依赖默认的回退 [`Broadcast.DefaultArrayStyle`](@ref)。

要覆盖这些默认值，您可以为您的对象定义一个自定义 `BroadcastStyle`：

```julia
struct MyStyle <: Broadcast.BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyType}) = MyStyle()
```

在某些情况下，可能不需要定义 `MyStyle`，在这种情况下，您可以利用其中一个通用广播包装器：

  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.Style{MyType}()` 可以用于任意类型。
  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.ArrayStyle{MyType}()` 如果 `MyType` 是 `AbstractArray`，则更为推荐。
  * 对于仅支持特定维度的 `AbstractArrays`，创建一个 `Broadcast.AbstractArrayStyle{N}` 的子类型（见下文）。

当您的广播操作涉及多个参数时，单个参数样式会组合以确定一个单一的 `DestStyle`，该样式控制输出容器的类型。有关更多详细信息，请参见 [below](@ref writing-binary-broadcasting-rules)。

### Selecting an appropriate output array

广播样式是为每个广播操作计算的，以便于调度和特化。结果数组的实际分配由 `similar` 处理，使用广播对象作为其第一个参数。

```julia
Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})
```

备用定义是

```julia
similar(bc::Broadcasted{DefaultArrayStyle{N}}, ::Type{ElType}) where {N,ElType} =
    similar(Array{ElType}, axes(bc))
```

然而，如果需要，您可以专注于这些参数中的任何一个或全部。最后一个参数 `bc` 是一个懒惰的表示（可能融合的）广播操作的 `Broadcasted` 对象。出于这些目的，包装器中最重要的字段是 `f` 和 `args`，分别描述函数和参数列表。请注意，参数列表可以——并且通常会——包含其他嵌套的 `Broadcasted` 包装器。

对于一个完整的示例，假设您创建了一个类型 `ArrayAndChar`，它存储一个数组和一个单个字符：

```jldoctest ArrayAndChar; output = false
struct ArrayAndChar{T,N} <: AbstractArray{T,N}
    data::Array{T,N}
    char::Char
end
Base.size(A::ArrayAndChar) = size(A.data)
Base.getindex(A::ArrayAndChar{T,N}, inds::Vararg{Int,N}) where {T,N} = A.data[inds...]
Base.setindex!(A::ArrayAndChar{T,N}, val, inds::Vararg{Int,N}) where {T,N} = A.data[inds...] = val
Base.showarg(io::IO, A::ArrayAndChar, toplevel) = print(io, typeof(A), " with char '", A.char, "'")
# output

```

您可能希望广播以保留 `char` "元数据"。首先我们定义

```jldoctest ArrayAndChar; output = false
Base.BroadcastStyle(::Type{<:ArrayAndChar}) = Broadcast.ArrayStyle{ArrayAndChar}()
# output

```

这意味着我们还必须定义一个相应的 `similar` 方法：

```jldoctest ArrayAndChar; output = false
function Base.similar(bc::Broadcast.Broadcasted{Broadcast.ArrayStyle{ArrayAndChar}}, ::Type{ElType}) where ElType
    # Scan the inputs for the ArrayAndChar:
    A = find_aac(bc)
    # Use the char field of A to create the output
    ArrayAndChar(similar(Array{ElType}, axes(bc)), A.char)
end

"`A = find_aac(As)` returns the first ArrayAndChar among the arguments."
find_aac(bc::Base.Broadcast.Broadcasted) = find_aac(bc.args)
find_aac(args::Tuple) = find_aac(find_aac(args[1]), Base.tail(args))
find_aac(x) = x
find_aac(::Tuple{}) = nothing
find_aac(a::ArrayAndChar, rest) = a
find_aac(::Any, rest) = find_aac(rest)
# output
find_aac (generic function with 6 methods)
```

从这些定义中，可以得到以下行为：

```jldoctest ArrayAndChar
julia> a = ArrayAndChar([1 2; 3 4], 'x')
2×2 ArrayAndChar{Int64, 2} with char 'x':
 1  2
 3  4

julia> a .+ 1
2×2 ArrayAndChar{Int64, 2} with char 'x':
 2  3
 4  5

julia> a .+ [5,10]
2×2 ArrayAndChar{Int64, 2} with char 'x':
  6   7
 13  14
```

### [Extending broadcast with custom implementations](@id extending-in-place-broadcast)

一般来说，广播操作由一个懒惰的 `Broadcasted` 容器表示，该容器持有要应用的函数及其参数。这些参数本身可能是更嵌套的 `Broadcasted` 容器，形成一个大型的表达式树以供评估。嵌套的 `Broadcasted` 容器树通过隐式点语法直接构造；例如，`5 .+ 2.*x` 暂时表示为 `Broadcasted(+, 5, Broadcasted(*, 2, x))`。这对用户是不可见的，因为它通过调用 `copy` 立即实现，但正是这个容器为自定义类型的作者提供了广播的可扩展性基础。内置的广播机制将根据参数确定结果类型和大小，分配它，然后最终将 `Broadcasted` 对象的实现复制到其中，使用默认的 `copyto!(::AbstractArray, ::Broadcasted)` 方法。内置的后备 `broadcast` 和 `broadcast!` 方法同样构造了操作的瞬态 `Broadcasted` 表示，以便它们可以遵循相同的代码路径。这允许自定义数组实现提供自己的 `copyto!` 特化，以自定义和优化广播。这再次由计算出的广播样式决定。这是操作中如此重要的一部分，以至于它作为 `Broadcasted` 类型的第一个类型参数存储，允许调度和特化。

对于某些类型，跨嵌套广播级别“融合”操作的机制不可用，或者可以更高效地逐步完成。在这种情况下，您可能需要或想要将 `x .* (x .+ 1)` 评估为好像它是写成 `broadcast(*, x, broadcast(+, x, 1))`，其中内部操作在处理外部操作之前被评估。这种急切操作通过一些间接支持；Julia 将融合的表达式 `x .* (x .+ 1)` 降低为 `Broadcast.broadcasted(*, x, Broadcast.broadcasted(+, x, 1))`。现在，默认情况下，`broadcasted` 只是调用 `Broadcasted` 构造函数来创建融合表达式树的惰性表示，但您可以选择为特定的函数和参数组合覆盖它。

作为一个例子，内置的 `AbstractRange` 对象使用这种机制来优化可以仅根据起始值、步长和长度（或停止）进行急切评估的广播表达式的片段，而不是计算每一个元素。就像所有其他机制一样，`broadcasted` 也计算并暴露其参数的组合广播样式，因此，您可以专门针对 `broadcasted(::DestStyle, f, args...)` 进行优化，而不是专门针对 `broadcasted(f, args...)`，以适应任何样式、函数和参数的组合。

例如，以下定义支持范围的否定：

```julia
broadcasted(::DefaultArrayStyle{1}, ::typeof(-), r::OrdinalRange) = range(-first(r), step=-step(r), length=length(r))
```

### [Extending in-place broadcasting](@id extending-in-place-broadcast)

就地广播可以通过定义适当的 `copyto!(dest, bc::Broadcasted)` 方法来支持。因为您可能想要专门针对 `dest` 或 `bc` 的特定子类型，为了避免包之间的歧义，我们建议遵循以下约定。

如果您希望专注于特定样式 `DestStyle`，请定义一个方法用于

```julia
copyto!(dest, bc::Broadcasted{DestStyle})
```

可选地，使用此表单您还可以专注于 `dest` 的类型。

如果您想专注于目标类型 `DestType` 而不专注于 `DestStyle`，那么您应该定义一个具有以下签名的方法：

```julia
copyto!(dest::DestType, bc::Broadcasted{Nothing})
```

这利用了 `copyto!` 的后备实现，将包装器转换为 `Broadcasted{Nothing}`。因此，针对 `DestType` 的特化优先级低于针对 `DestStyle` 的方法特化。

同样，您可以通过 `copy(::Broadcasted)` 方法完全覆盖不合适的广播。

#### Working with `Broadcasted` objects

为了实现这样的 `copy` 或 `copyto!` 方法，当然，您必须使用 `Broadcasted` 包装器来计算每个元素。主要有两种方法可以做到这一点：

  * `Broadcast.flatten` 重新计算潜在嵌套的操作为一个单一的函数和扁平的参数列表。您需要自己实现广播形状规则，但在有限的情况下，这可能会有所帮助。
  * 遍历 `axes(::Broadcasted)` 的 `CartesianIndices`，并使用结果 `CartesianIndex` 对象进行索引以计算结果。

### [Writing binary broadcasting rules](@id writing-binary-broadcasting-rules)

优先级规则由二进制 `BroadcastStyle` 调用定义：

```julia
Base.BroadcastStyle(::Style1, ::Style2) = Style12()
```

其中 `Style12` 是您想为涉及 `Style1` 和 `Style2` 参数的输出选择的 `BroadcastStyle`。例如，

```julia
Base.BroadcastStyle(::Broadcast.Style{Tuple}, ::Broadcast.AbstractArrayStyle{0}) = Broadcast.Style{Tuple}()
```

表明 `Tuple` "胜过" 零维数组（输出容器将是一个元组）。值得注意的是，您不需要（也不应该）定义此调用的两种参数顺序；定义一种就足够了，无论用户以何种顺序提供参数。

对于 `AbstractArray` 类型，定义 `BroadcastStyle` 取代了后备选择 [`Broadcast.DefaultArrayStyle`](@ref)。`DefaultArrayStyle` 和 抽象超类型 `AbstractArrayStyle` 将维度存储为类型参数，以支持具有固定维度要求的专用数组类型。

`DefaultArrayStyle` "输给" 任何其他已定义的 `AbstractArrayStyle`，原因如下：

```julia
BroadcastStyle(a::AbstractArrayStyle{Any}, ::DefaultArrayStyle) = a
BroadcastStyle(a::AbstractArrayStyle{N}, ::DefaultArrayStyle{N}) where N = a
BroadcastStyle(a::AbstractArrayStyle{M}, ::DefaultArrayStyle{N}) where {M,N} =
    typeof(a)(Val(max(M, N)))
```

您不需要编写二进制 `BroadcastStyle` 规则，除非您想为两个或多个非 `DefaultArrayStyle` 类型建立优先级。

如果您的数组类型确实有固定的维度要求，那么您应该子类化 `AbstractArrayStyle`。例如，稀疏数组代码具有以下定义：

```julia
struct SparseVecStyle <: Broadcast.AbstractArrayStyle{1} end
struct SparseMatStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseVector}) = SparseVecStyle()
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatStyle()
```

每当你子类化 `AbstractArrayStyle` 时，你还需要通过创建一个接受 `Val(N)` 参数的构造函数来定义组合维度的规则。例如：

```julia
SparseVecStyle(::Val{0}) = SparseVecStyle()
SparseVecStyle(::Val{1}) = SparseVecStyle()
SparseVecStyle(::Val{2}) = SparseMatStyle()
SparseVecStyle(::Val{N}) where N = Broadcast.DefaultArrayStyle{N}()
```

这些规则表明，`SparseVecStyle`与0维或1维数组的组合会产生另一个`SparseVecStyle`，与2维数组的组合会产生`SparseMatStyle`，而任何更高维度的组合则会回退到稠密的任意维度框架。这些规则允许广播在结果为一维或二维输出的操作中保持稀疏表示，但对于任何其他维度则会生成一个`Array`。

## [Instance Properties](@id man-instance-properties)

| Methods to implement                             | Default definition      | Brief description                                                                                                                              |
|:------------------------------------------------ |:----------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------- |
| `propertynames(x::ObjType, private::Bool=false)` | `fieldnames(typeof(x))` | Return a tuple of the properties (`x.property`) of an object `x`. If `private=true`, also return property names intended to be kept as private |
| `getproperty(x::ObjType, s::Symbol)`             | `getfield(x, s)`        | Return property `s` of `x`. `x.s` calls `getproperty(x, :s)`.                                                                                  |
| `setproperty!(x::ObjType, s::Symbol, v)`         | `setfield!(x, s, v)`    | Set property `s` of `x` to `v`. `x.s = v` calls `setproperty!(x, :s, v)`. Should return `v`.                                                   |

有时，改变最终用户与对象字段的交互方式是可取的。与其直接访问类型字段，不如通过重载 `object.field` 提供用户与代码之间的额外抽象层。属性是用户 *看到的* 对象，而字段是对象 *实际的* 形态。

默认情况下，属性和字段是相同的。然而，这种行为可以改变。例如，考虑在 [polar coordinates](https://en.wikipedia.org/wiki/Polar_coordinate_system) 中表示平面上的一个点：

```jldoctest polartype
julia> mutable struct Point
           r::Float64
           ϕ::Float64
       end

julia> p = Point(7.0, pi/4)
Point(7.0, 0.7853981633974483)
```

如上表所述，点访问 `p.r` 与 `getproperty(p, :r)` 是相同的，默认情况下与 `getfield(p, :r)` 也是相同的：

```jldoctest polartype
julia> propertynames(p)
(:r, :ϕ)

julia> getproperty(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)

julia> p.r, p.ϕ
(7.0, 0.7853981633974483)

julia> getfield(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)
```

然而，我们可能希望用户不知道 `Point` 将坐标存储为 `r` 和 `ϕ`（字段），而是与 `x` 和 `y`（属性）进行交互。第一列中的方法可以被定义为添加新功能：

```jldoctest polartype
julia> Base.propertynames(::Point, private::Bool=false) = private ? (:x, :y, :r, :ϕ) : (:x, :y)

julia> function Base.getproperty(p::Point, s::Symbol)
           if s === :x
               return getfield(p, :r) * cos(getfield(p, :ϕ))
           elseif s === :y
               return getfield(p, :r) * sin(getfield(p, :ϕ))
           else
               # This allows accessing fields with p.r and p.ϕ
               return getfield(p, s)
           end
       end

julia> function Base.setproperty!(p::Point, s::Symbol, f)
           if s === :x
               y = p.y
               setfield!(p, :r, sqrt(f^2 + y^2))
               setfield!(p, :ϕ, atan(y, f))
               return f
           elseif s === :y
               x = p.x
               setfield!(p, :r, sqrt(x^2 + f^2))
               setfield!(p, :ϕ, atan(f, x))
               return f
           else
               # This allow modifying fields with p.r and p.ϕ
               return setfield!(p, s, f)
           end
       end
```

重要的是在 `getproperty` 和 `setproperty!` 中使用 `getfield` 和 `setfield`，而不是点语法，因为点语法会使函数递归，这可能导致类型推断问题。我们现在可以尝试新功能：

```jldoctest polartype
julia> propertynames(p)
(:x, :y)

julia> p.x
4.949747468305833

julia> p.y = 4.0
4.0

julia> p.r
6.363961030678928
```

最后，值得注意的是，在Julia中像这样添加实例属性是非常少见的，通常只有在有充分理由的情况下才应该这样做。

## [Rounding](@id man-rounding-interface)

| Methods to implement                          | Default definition        | Brief description                                                                                   |
|:--------------------------------------------- |:------------------------- |:--------------------------------------------------------------------------------------------------- |
| `round(x::ObjType, r::RoundingMode)`          | none                      | Round `x` and return the result. If possible, round should return an object of the same type as `x` |
| `round(T::Type, x::ObjType, r::RoundingMode)` | `convert(T, round(x, r))` | Round `x`, returning the result as a `T`                                                            |

要支持新类型的舍入，通常只需定义单个方法 `round(x::ObjType, r::RoundingMode)`。传递的舍入模式决定了值应朝哪个方向舍入。最常用的舍入模式是 `RoundNearest`、`RoundToZero`、`RoundDown` 和 `RoundUp`，因为这些舍入模式分别用于定义一个参数的 `round` 方法，以及 `trunc`、`floor` 和 `ceil`。

在某些情况下，可以定义一个三参数的 `round` 方法，该方法比后续转换的两参数方法更准确或更高效。在这种情况下，除了两参数方法外，定义三参数方法是可以接受的。如果无法将四舍五入的结果表示为类型 `T` 的对象，则三参数方法应抛出 `InexactError`。

例如，如果我们有一个 `Interval` 类型，它表示一个可能值的范围，类似于 https://github.com/JuliaPhysics/Measurements.jl，我们可以用以下方式在该类型上定义舍入：

```jldoctest
julia> struct Interval{T}
           min::T
           max::T
       end

julia> Base.round(x::Interval, r::RoundingMode) = Interval(round(x.min, r), round(x.max, r))

julia> x = Interval(1.7, 2.2)
Interval{Float64}(1.7, 2.2)

julia> round(x)
Interval{Float64}(2.0, 2.0)

julia> floor(x)
Interval{Float64}(1.0, 2.0)

julia> ceil(x)
Interval{Float64}(2.0, 3.0)

julia> trunc(x)
Interval{Float64}(1.0, 2.0)
```
