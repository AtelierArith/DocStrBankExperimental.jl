# Sorting and Related Functions

Julia 拥有一个广泛且灵活的 API，用于对已排序的值数组进行排序和交互。默认情况下，Julia 选择合理的算法并按升序排序：

```jldoctest
julia> sort([2,3,1])
3-element Vector{Int64}:
 1
 2
 3
```

您也可以按相反顺序排序：

```jldoctest
julia> sort([2,3,1], rev=true)
3-element Vector{Int64}:
 3
 2
 1
```

`sort` 构造一个已排序的副本，保持其输入不变。使用 "bang" 版本的排序函数来改变现有数组：

```jldoctest
julia> a = [2,3,1];

julia> sort!(a);

julia> a
3-element Vector{Int64}:
 1
 2
 3
```

而不是直接对数组进行排序，您可以计算一个数组索引的排列，使数组按排序顺序排列：

```julia-repl
julia> v = randn(5)
5-element Array{Float64,1}:
  0.297288
  0.382396
 -0.597634
 -0.0104452
 -0.839027

julia> p = sortperm(v)
5-element Array{Int64,1}:
 5
 3
 4
 1
 2

julia> v[p]
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

数组可以根据其值的任意变换进行排序：

```julia-repl
julia> sort(v, by=abs)
5-element Array{Float64,1}:
 -0.0104452
  0.297288
  0.382396
 -0.597634
 -0.839027
```

或通过变换以相反的顺序：

```julia-repl
julia> sort(v, by=abs, rev=true)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
  0.382396
  0.297288
 -0.0104452
```

如果需要，可以选择排序算法：

```julia-repl
julia> sort(v, alg=InsertionSort)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

所有与排序和顺序相关的函数都依赖于一个“少于”关系，定义了一个 [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings)，用于要操作的值。默认情况下调用 `isless` 函数，但可以通过 `lt` 关键字指定关系，该函数接受两个数组元素，并仅在第一个参数“少于”第二个时返回 `true`。有关更多信息，请参见 [`sort!`](@ref) 和 [Alternate Orderings](@ref)。

## Sorting Functions

```@docs
Base.sort!
Base.sort
Base.sortperm
Base.InsertionSort
Base.MergeSort
Base.QuickSort
Base.PartialQuickSort
Base.Sort.sortperm!
Base.Sort.sortslices
```

## Order-Related Functions

```@docs
Base.issorted
Base.Sort.searchsorted
Base.Sort.searchsortedfirst
Base.Sort.searchsortedlast
Base.Sort.insorted
Base.Sort.partialsort!
Base.Sort.partialsort
Base.Sort.partialsortperm
Base.Sort.partialsortperm!
```

## Sorting Algorithms

目前在基础 Julia 中公开可用的四种排序算法：

  * [`InsertionSort`](@ref)
  * [`QuickSort`](@ref)
  * [`PartialQuickSort(k)`](@ref)
  * [`MergeSort`](@ref)

默认情况下，`sort` 函数族使用在大多数输入上都很快的稳定排序算法。确切的算法选择是一个实现细节，以便于未来的性能改进。目前，根据输入类型、大小和组成，使用 `RadixSort`、`ScratchQuickSort`、`InsertionSort` 和 `CountingSort` 的混合体。实现细节可能会发生变化，但目前可以在 `??Base.DEFAULT_STABLE` 的扩展帮助和那里列出的内部排序算法的文档字符串中找到。

您可以通过 `alg` 关键字明确指定您首选的算法（例如 `sort!(v, alg=PartialQuickSort(10:20))`），或者通过向 `Base.Sort.defalg` 函数添加专门的方法来重新配置自定义类型的默认排序算法。例如，[InlineStrings.jl](https://github.com/JuliaStrings/InlineStrings.jl/blob/v1.3.2/src/InlineStrings.jl#L903) 定义了以下方法：

```julia
Base.Sort.defalg(::AbstractArray{<:Union{SmallInlineStrings, Missing}}) = InlineStringSort
```

!!! compat "Julia 1.9"
    默认的排序算法（由 `Base.Sort.defalg` 返回）自 Julia 1.9 起保证是稳定的。之前的版本在排序数字数组时存在不稳定的边缘情况。


## Alternate Orderings

默认情况下，`sort`、`searchsorted` 和相关函数使用 [`isless`](@ref) 来比较两个元素，以确定哪个应该先出现。[`Base.Order.Ordering`](@ref) 抽象类型提供了一种机制，用于在同一组元素上定义替代排序：在调用像 `sort!` 这样的排序函数时，可以通过关键字参数 `order` 提供一个 `Ordering` 的实例。

`Ordering` 的实例通过 [`Base.Order.lt`](@ref) 函数定义了一个顺序，该函数作为 `isless` 的一种推广。此函数在自定义 `Ordering` 上的行为必须满足 [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings) 的所有条件。有关有效和无效 `lt` 函数的详细信息和示例，请参见 [`sort!`](@ref)。

```@docs
Base.Order.Ordering
Base.Order.lt
Base.Order.ord
Base.Order.Forward
Base.Order.ReverseOrdering
Base.Order.Reverse
Base.Order.By
Base.Order.Lt
Base.Order.Perm
```
