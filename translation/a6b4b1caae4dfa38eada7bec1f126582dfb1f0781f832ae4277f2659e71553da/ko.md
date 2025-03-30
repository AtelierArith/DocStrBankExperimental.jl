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

또한 [dot syntax for vectorizing functions](@ref man-vectorized)를 참조하십시오. 예를 들어, `f.(args...)`는 암묵적으로 `broadcast(f, args...)`를 호출합니다. `sin`과 같은 함수의 "벡터화된" 메서드에 의존하기보다는, `sin.(a)`를 사용하여 `broadcast`를 통해 벡터화해야 합니다.

```@docs
Base.broadcast
Base.Broadcast.broadcast!
Base.@__dot__
```

사용자 정의 유형에 대한 전문 방송을 보려면 다음을 참조하십시오.

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

“뷰(view)”는 배열처럼 작동하는 데이터 구조(‘AbstractArray’의 하위 유형)지만, 기본 데이터는 실제로 다른 배열의 일부입니다.

예를 들어, `x`가 배열이고 `v = @view x[1:10]`인 경우, `v`는 10개 요소를 가진 배열처럼 작동하지만, 실제로는 `x`의 첫 10개 요소에 접근하고 있습니다. 뷰에 쓰기를 하면, 예를 들어 `v[3] = 2`는 기본 배열 `x`에 직접 쓰기를 하며 (이 경우 `x[3]`를 수정하게 됩니다).

슬라이싱 작업은 기본적으로 Julia에서 `x[1:10]`와 같이 복사본을 생성합니다. `@view x[1:10]`는 이를 뷰로 변경합니다. `@views` 매크로는 전체 코드 블록에 사용할 수 있으며(예: `@views function foo() .... end` 또는 `@views begin ... end`), 해당 블록의 모든 슬라이싱 작업을 뷰를 사용하도록 변경합니다. 때때로 데이터의 복사본을 만드는 것이 더 빠르고, 때때로 뷰를 사용하는 것이 더 빠릅니다. 이는 [performance tips](@ref man-performance-views)에서 설명됩니다.

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
