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

Siehe auch die [dot syntax for vectorizing functions](@ref man-vectorized); zum Beispiel ruft `f.(args...)` implizit `broadcast(f, args...)` auf. Anstatt sich auf "vektorisierte" Methoden von Funktionen wie `sin` zu verlassen, die auf Arrays wirken, sollten Sie `sin.(a)` verwenden, um über `broadcast` zu vektorisieren.

```@docs
Base.broadcast
Base.Broadcast.broadcast!
Base.@__dot__
```

Für die Spezialisierung von Broadcast auf benutzerdefinierte Typen siehe

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

Ein „View“ ist eine Datenstruktur, die sich wie ein Array verhält (es ist ein Subtyp von `AbstractArray`), aber die zugrunde liegenden Daten sind tatsächlich Teil eines anderen Arrays.

Zum Beispiel, wenn `x` ein Array ist und `v = @view x[1:10]`, dann verhält sich `v` wie ein 10-Elemente-Array, aber seine Daten greifen tatsächlich auf die ersten 10 Elemente von `x` zu. Das Schreiben in eine Ansicht, z.B. `v[3] = 2`, schreibt direkt in das zugrunde liegende Array `x` (in diesem Fall wird `x[3]` modifiziert).

Slicing-Operationen wie `x[1:10]` erstellen standardmäßig eine Kopie in Julia. `@view x[1:10]` ändert dies, um eine Ansicht zu erstellen. Das `@views`-Makro kann auf einen ganzen Codeblock angewendet werden (z. B. `@views function foo() .... end` oder `@views begin ... end`), um alle Slicing-Operationen in diesem Block so zu ändern, dass sie Ansichten verwenden. Manchmal ist das Erstellen einer Kopie der Daten schneller und manchmal ist die Verwendung einer Ansicht schneller, wie in der [performance tips](@ref man-performance-views) beschrieben.

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
