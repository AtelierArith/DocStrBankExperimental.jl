# Bounds checking

像许多现代编程语言一样，Julia 使用边界检查来确保在访问数组时程序的安全性。在紧密的内循环或其他性能关键的情况下，您可能希望跳过这些边界检查以提高运行时性能。例如，为了发出向量化（SIMD）指令，您的循环体不能包含分支，因此不能包含边界检查。因此，Julia 包含一个 `@inbounds(...)` 宏，以告诉编译器在给定块内跳过这些边界检查。用户定义的数组类型可以使用 `@boundscheck(...)` 宏来实现上下文敏感的代码选择。

## Eliding bounds checks

`@boundscheck(...)` 宏标记执行边界检查的代码块。当这样的代码块被内联到 `@inbounds(...)` 块中时，编译器可能会移除这些代码块。编译器仅在 `@boundscheck` 块被内联到调用函数中时才会移除它。比如，你可以将方法 `sum` 写成：

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

具有自定义数组类型 `MyArray`，其包含：

```julia
@inline getindex(A::MyArray, i::Real) = (@boundscheck checkbounds(A, i); A.data[to_index(i)])
```

然后，当 `getindex` 被内联到 `sum` 中时，对 `checkbounds(A, i)` 的调用将被省略。如果你的函数包含多个内联层次，只有 `@boundscheck` 块在最多一个内联层次更深的地方被消除。这个规则防止了来自栈上更高层代码的意外行为变化。

### Caution!

很容易不小心暴露使用 `@inbounds` 的不安全操作。你可能会想将上述示例写成

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in 1:length(A)
        @inbounds r += A[i]
    end
    return r
end
```

哪个默默假设了基于1的索引，因此在与 [`OffsetArrays`](@ref man-custom-indices) 一起使用时暴露了不安全的内存访问：

```julia-repl
julia> using OffsetArrays

julia> sum(OffsetArray([1, 2, 3], -10))
9164911648 # inconsistent results or segfault
```

虽然这里错误的原始来源是 `1:length(A)`，但使用 `@inbounds` 将边界错误的后果从一个容易捕获和调试的错误提升到了一个不那么容易捕获和调试的不安全内存访问。通常很难或不可能证明使用 `@inbounds` 的方法是安全的，因此必须权衡性能提升的好处与段错误和静默错误行为的风险，特别是在面向公众的 API 中。

## Propagating inbounds

在某些情况下，由于代码组织的原因，您可能希望在 `@inbounds` 和 `@boundscheck` 声明之间有多个层次。例如，默认的 `getindex` 方法具有链 `getindex(A::AbstractArray, i::Real)` 调用 `getindex(IndexStyle(A), A, i)` 调用 `_getindex(::IndexLinear, A, i)`。

要覆盖“单层内联”规则，可以将函数标记为 [`Base.@propagate_inbounds`](@ref) 以通过额外一层内联传播一个边界内上下文（或越界上下文）。

## The bounds checking call hierarchy

整体层级是：

  * `checkbounds(A, I...)` 调用

      * `checkbounds(Bool, A, I...)` 调用

          * `checkbounds_indices(Bool, axes(A), I)` 递归调用

              * `checkindex` 对于每个维度

这里 `A` 是数组，`I` 包含“请求的”索引。`axes(A)` 返回 `A` 的“允许的”索引元组。

`checkbounds(A, I...)` 在索引无效时会抛出错误，而 `checkbounds(Bool, A, I...)` 在这种情况下返回 `false`。 `checkbounds_indices` 丢弃了关于数组的任何信息，除了它的 `axes` 元组，并执行纯粹的索引与索引的比较：这允许相对较少的编译方法服务于大量的数组类型。索引被指定为元组，通常以 1-1 的方式进行比较，个别维度通过调用另一个重要函数 `checkindex` 来处理：通常，

```julia
checkbounds_indices(Bool, (IA1, IA...), (I1, I...)) = checkindex(Bool, IA1, I1) &
                                                      checkbounds_indices(Bool, IA, I)
```

所以 `checkindex` 检查单个维度。所有这些函数，包括未导出的 `checkbounds_indices`，都有可以通过 `?` 访问的文档字符串。

如果您需要为特定数组类型自定义边界检查，您应该专门化 `checkbounds(Bool, A, I...)`。然而，在大多数情况下，只要您为您的数组类型提供有用的 `axes`，您应该能够依赖 `checkbounds_indices`。

如果您有新颖的索引类型，首先考虑专门化 `checkindex`，它处理数组特定维度的单个索引。如果您有自定义的多维索引类型（类似于 `CartesianIndex`），那么您可能需要考虑专门化 `checkbounds_indices`。

请注意，这个层次结构的设计旨在减少方法歧义的可能性。我们尝试使 `checkbounds` 成为专注于数组类型的地方，并尽量避免对索引类型的专门化；相反，`checkindex` 旨在仅对索引类型（特别是最后一个参数）进行专门化。

## Emit bounds checks

Julia 可以通过 `--check-bounds={yes|no|auto}` 启动，以始终、从不或尊重 `@inbounds` 声明来发出边界检查。
