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

Ayrıca [dot syntax for vectorizing functions](@ref man-vectorized)'e bakın; örneğin, `f.(args...)` aslında `broadcast(f, args...)`'i çağırır. `sin` gibi fonksiyonların diziler üzerinde çalışması için "vektörleştirilmiş" yöntemlere güvenmek yerine, `broadcast` aracılığıyla vektörleştirmek için `sin.(a)` kullanmalısınız.

```@docs
Base.broadcast
Base.Broadcast.broadcast!
Base.@__dot__
```

Özel türler üzerinde yayın yapma için, bakınız

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

Bir “görünüm”, bir dizi gibi davranan bir veri yapısıdır (bu, `AbstractArray`'ın bir alt türüdür), ancak temel veri aslında başka bir dizinin parçasıdır.

Örneğin, eğer `x` bir dizi ise ve `v = @view x[1:10]` ise, o zaman `v` 10 elemanlı bir dizi gibi davranır, ancak verileri aslında `x`'in ilk 10 elemanına erişmektedir. Bir görünüme yazmak, örneğin `v[3] = 2`, doğrudan temel dizi `x`'e yazar (bu durumda `x[3]`'ü değiştirir).

Kesme işlemleri `x[1:10]` gibi varsayılan olarak Julia'da bir kopya oluşturur. `@view x[1:10]` bunu bir görünüm oluşturacak şekilde değiştirir. `@views` makrosu, o bloktaki tüm kesme işlemlerini görünüm kullanacak şekilde değiştirmek için bir kod bloğunun tamamında (örneğin, `@views function foo() .... end` veya `@views begin ... end`) kullanılabilir. Bazen verilerin bir kopyasını oluşturmak daha hızlıdır ve bazen de bir görünüm kullanmak daha hızlıdır; bu, [performance tips](@ref man-performance-views) içinde açıklanmıştır.

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
