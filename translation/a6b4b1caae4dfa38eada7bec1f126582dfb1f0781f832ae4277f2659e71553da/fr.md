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

Voir aussi le [dot syntax for vectorizing functions](@ref man-vectorized); par exemple, `f.(args...)` appelle implicitement `broadcast(f, args...)`. Plutôt que de s'appuyer sur des méthodes "vectorisées" de fonctions comme `sin` pour opérer sur des tableaux, vous devriez utiliser `sin.(a)` pour vectoriser via `broadcast`.

```@docs
Base.broadcast
Base.Broadcast.broadcast!
Base.@__dot__
```

Pour se spécialiser dans la diffusion sur des types personnalisés, voir

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

Une « vue » est une structure de données qui agit comme un tableau (c'est un sous-type de `AbstractArray`), mais les données sous-jacentes font en réalité partie d'un autre tableau.

Par exemple, si `x` est un tableau et `v = @view x[1:10]`, alors `v` agit comme un tableau de 10 éléments, mais ses données accèdent en réalité aux 10 premiers éléments de `x`. Écrire dans une vue, par exemple `v[3] = 2`, écrit directement dans le tableau sous-jacent `x` (dans ce cas, modifiant `x[3]`).

Les opérations de découpage comme `x[1:10]` créent une copie par défaut en Julia. `@view x[1:10]` le change pour en faire une vue. Le macro `@views` peut être utilisé sur un bloc de code entier (par exemple, `@views function foo() .... end` ou `@views begin ... end`) pour changer toutes les opérations de découpage dans ce bloc afin d'utiliser des vues. Parfois, faire une copie des données est plus rapide et parfois utiliser une vue est plus rapide, comme décrit dans le [performance tips](@ref man-performance-views).

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
