`Broadcast.AbstractArrayStyle{N} <: BroadcastStyle` ist der abstrakte Supertyp für jeden Stil, der mit einem `AbstractArray`-Typ verbunden ist. Der Parameter `N` ist die Dimensionalität, die nützlich sein kann für AbstractArray-Typen, die nur bestimmte Dimensionalitäten unterstützen:

```
struct SparseMatrixStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatrixStyle()
```

Für `AbstractArray`-Typen, die beliebige Dimensionalität unterstützen, kann `N` auf `Any` gesetzt werden:

```
struct MyArrayStyle <: Broadcast.AbstractArrayStyle{Any} end
Base.BroadcastStyle(::Type{<:MyArray}) = MyArrayStyle()
```

In Fällen, in denen Sie mehrere `AbstractArrayStyle`s mischen und die Dimensionalität im Auge behalten möchten, muss Ihr Stil einen [`Val`](@ref) Konstruktor unterstützen:

```
struct MyArrayStyleDim{N} <: Broadcast.AbstractArrayStyle{N} end
(::Type{<:MyArrayStyleDim})(::Val{N}) where N = MyArrayStyleDim{N}()
```

Beachten Sie, dass, wenn zwei oder mehr `AbstractArrayStyle`-Subtypen in Konflikt stehen, die Broadcast-Mechanik auf die Erzeugung von `Array`s zurückgreift. Wenn dies unerwünscht ist, müssen Sie möglicherweise binäre [`BroadcastStyle`](@ref) Regeln definieren, um den Ausgabetyp zu steuern.

Siehe auch [`Broadcast.DefaultArrayStyle`](@ref).
