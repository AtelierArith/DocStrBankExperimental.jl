# [Arrays with custom indices](@id man-custom-indices)

传统上，Julia 的数组索引从 1 开始，而其他一些语言则从 0 开始编号，还有一些语言（例如 Fortran）允许您指定任意起始索引。虽然选择一个标准（即 Julia 的 1）有很多优点，但有些算法在您可以在 `1:size(A,d)` 范围之外进行索引时会大大简化（而不仅仅是 `0:size(A,d)-1`）。为了方便这样的计算，Julia 支持具有任意索引的数组。

此页面的目的是回答“我需要做什么才能在自己的代码中支持这样的数组？”这个问题。首先，让我们处理最简单的情况：如果你知道你的代码永远不需要处理具有非常规索引的数组，那么希望答案是“什么都不需要”。旧代码在常规数组上应该基本上可以正常工作，只要它使用的是Julia的导出接口。如果你发现强迫用户提供传统数组（索引从1开始）更方便，你可以添加

```julia
Base.require_one_based_indexing(arrays...)
```

其中 `arrays...` 是您希望检查是否违反 1 基索引的数组对象列表。

## Generalizing existing code

作为概述，步骤如下：

  * 请提供您想要翻译的Markdown内容。
  * 将 `1:length(A)` 替换为 `eachindex(A)`，或在某些情况下使用 `LinearIndices(A)`。
  * 将显式分配如 `Array{Int}(undef, size(B))` 替换为 `similar(Array{Int}, axes(B))`

这些将在下面更详细地描述。

### Things to watch out for

因为非常规索引打破了许多人认为所有数组都从1开始索引的假设，因此使用这样的数组总是有可能触发错误。最令人沮丧的错误可能是错误的结果或段错误（Julia的完全崩溃）。例如，考虑以下函数：

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    length(dest) == length(src) || throw(DimensionMismatch("vectors must match"))
    # OK, now we're safe to use @inbounds, right? (not anymore!)
    for i = 1:length(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

此代码隐含地假设向量的索引从 1 开始；如果 `dest` 的起始索引与 `src` 不同，则有可能触发段错误（segfault）。 （如果您确实遇到段错误，请尝试使用选项 `--check-bounds=yes` 运行 julia，以帮助定位原因。）

### Using `axes` for bounds checks and loop iteration

`axes(A)`（类似于 `size(A)`）返回一个 `AbstractUnitRange{<:Integer}` 对象的元组，指定 `A` 每个维度的有效索引范围。当 `A` 具有非常规索引时，范围可能不会从 1 开始。如果您只想要特定维度 `d` 的范围，可以使用 `axes(A, d)`。

Base 实现了一个自定义范围类型 `OneTo`，其中 `OneTo(n)` 的意思与 `1:n` 相同，但以一种通过类型系统保证下标为 1 的形式表示。对于任何新的 [`AbstractArray`](@ref) 类型，这是 `axes` 返回的默认值，表示该数组类型使用“常规”的 1 基索引。

对于边界检查，请注意有专门的函数 `checkbounds` 和 `checkindex`，它们有时可以简化此类测试。

### Linear indexing (`LinearIndices`)

一些算法最方便（或高效）地用单个线性索引 `A[i]` 来编写，即使 `A` 是多维的。无论数组的原生索引如何，线性索引始终范围从 `1:length(A)`。然而，这对一维数组（即 [`AbstractVector`](@ref)）提出了一个模糊性：`v[i]` 是指线性索引，还是使用数组的原生索引的笛卡尔索引？

出于这个原因，您最好的选择可能是使用 `eachindex(A)` 遍历数组，或者，如果您需要索引为连续整数，可以通过调用 `LinearIndices(A)` 来获取索引范围。如果 A 是 AbstractVector，这将返回 `axes(A, 1)`，否则将返回 `1:length(A)` 的等效值。

根据这个定义，1维数组始终使用数组的本地索引进行笛卡尔索引。为了帮助强制执行这一点，值得注意的是，如果形状指示一个具有非常规索引的1维数组（即，是一个`Tuple{UnitRange}`而不是`OneTo`的元组），索引转换函数将抛出错误。对于具有常规索引的数组，这些函数的工作方式与以往相同。

使用 `axes` 和 `LinearIndices`，以下是您可以重写 `mycopy!` 的一种方法：

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    axes(dest) == axes(src) || throw(DimensionMismatch("vectors must match"))
    for i in LinearIndices(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

### Allocating storage using generalizations of `similar`

存储通常使用 `Array{Int}(undef, dims)` 或 `similar(A, args...)` 进行分配。当结果需要与其他数组的索引匹配时，这可能并不总是足够。此类模式的通用替代方案是使用 `similar(storagetype, shape)`。`storagetype` 表示您希望的底层“常规”行为的类型，例如 `Array{Int}` 或 `BitArray`，甚至是 `dims->zeros(Float32, dims)`（这将分配一个全零数组）。`shape` 是一个 [`Integer`](@ref) 或 `AbstractUnitRange` 值的元组，指定您希望结果使用的索引。请注意，生成一个与 A 的索引匹配的全零数组的便捷方法是简单地使用 `zeros(A)`。

让我们通过几个明确的例子来说明。首先，如果 `A` 具有常规索引，则 `similar(Array{Int}, axes(A))` 最终会调用 `Array{Int}(undef, size(A))`，因此返回一个数组。如果 `A` 是一个具有非常规索引的 `AbstractArray` 类型，则 `similar(Array{Int}, axes(A))` 应该返回某种“表现得像” `Array{Int}` 的东西，但其形状（包括索引）与 `A` 匹配。（最明显的实现是分配一个 `Array{Int}(undef, size(A))`，然后将其“包装”在一个类型中，以便移动索引。）

请注意，`similar(Array{Int}, (axes(A, 2),))` 将分配一个与 `A` 的列索引匹配的 `AbstractVector{Int}`（即，1维数组）。

## Writing custom array types with non-1 indexing

您需要定义的大多数方法对于任何 `AbstractArray` 类型都是标准的，请参见 [Abstract Arrays](@ref man-interface-array)。本页面重点介绍定义非常规索引所需的步骤。

### Custom `AbstractUnitRange` types

如果您正在编写一个非1索引的数组类型，您将希望专门化 `axes` 以返回 `UnitRange`，或者（也许更好）一个自定义的 `AbstractUnitRange`。自定义类型的优点在于它为像 `similar` 这样的函数“信号”分配类型。如果我们正在编写一个索引从0开始的数组类型，我们可能希望首先创建一个新的 `AbstractUnitRange`，`ZeroRange`，其中 `ZeroRange(n)` 等价于 `0:n-1`。

一般来说，您可能*不*应该从您的包中导出 `ZeroRange`：可能还有其他包实现了他们自己的 `ZeroRange`，而拥有多个不同的 `ZeroRange` 类型（也许反直觉）是一个优势：`ModuleA.ZeroRange` 表示 `similar` 应该创建一个 `ModuleA.ZeroArray`，而 `ModuleB.ZeroRange` 表示一个 `ModuleB.ZeroArray` 类型。 这种设计允许许多不同自定义数组类型的和平共处。

请注意，Julia 包 [CustomUnitRanges.jl](https://github.com/JuliaArrays/CustomUnitRanges.jl) 有时可以用来避免需要自己编写 `ZeroRange` 类型。

### Specializing `axes`

一旦你拥有了 `AbstractUnitRange` 类型，就可以专门化 `axes`：

```julia
Base.axes(A::ZeroArray) = map(n->ZeroRange(n), A.size)
```

在这里，我们假设 `ZeroArray` 有一个名为 `size` 的字段（还有其他方法可以实现这一点）。

在某些情况下，`axes(A, d)` 的后备定义：

```julia
axes(A::AbstractArray{T,N}, d) where {T,N} = d <= N ? axes(A)[d] : OneTo(1)
```

可能不是你想要的：当 `d > ndims(A)` 时，你可能需要对其进行专门化，以返回除 `OneTo(1)` 以外的其他内容。同样，在 `Base` 中有一个专门的函数 `axes1`，它等同于 `axes(A, 1)`，但避免在运行时检查 `ndims(A) > 0`。 （这纯粹是性能优化。）它被定义为：

```julia
axes1(A::AbstractArray{T,0}) where {T} = OneTo(1)
axes1(A::AbstractArray) = axes(A)[1]
```

如果这些中的第一个（零维情况）对您的自定义数组类型有问题，请确保适当地对其进行特化。

### Specializing `similar`

鉴于您的自定义 `ZeroRange` 类型，您还应该为 `similar` 添加以下两个特化：

```julia
function Base.similar(A::AbstractArray, T::Type, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end

function Base.similar(f::Union{Function,DataType}, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end
```

这两者都应该分配你的自定义数组类型。

### Specializing `reshape`

可选地，定义一个方法

```
Base.reshape(A::AbstractArray, shape::Tuple{ZeroRange,Vararg{ZeroRange}}) = ...
```

你可以 `reshape` 一个数组，使得结果具有自定义索引。

### For objects that mimic AbstractArray but are not subtypes

`has_offset_axes` 依赖于为您调用它的对象定义 `axes`。如果您没有为您的对象定义 `axes` 方法，请考虑定义一个方法。

```julia
Base.has_offset_axes(obj::MyNon1IndexedArraylikeObject) = true
```

这将允许假设使用1基索引的代码检测问题并抛出有用的错误，而不是返回不正确的结果或导致Julia崩溃。

### Catching errors

如果您的新数组类型在其他代码中触发错误，一个有用的调试步骤是注释掉 `@boundscheck` 在您的 `getindex` 和 `setindex!` 实现中。这将确保每个元素访问都检查边界。或者，使用 `--check-bounds=yes` 重新启动 julia。

在某些情况下，暂时禁用新数组类型的 `size` 和 `length` 可能也会有所帮助，因为经常使用这些函数的代码会做出错误的假设。
