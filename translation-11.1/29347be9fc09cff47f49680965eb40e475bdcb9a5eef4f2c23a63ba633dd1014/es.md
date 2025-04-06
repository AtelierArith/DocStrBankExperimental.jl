`Broadcast.AbstractArrayStyle{N} <: BroadcastStyle` es el supertipo abstracto para cualquier estilo asociado con un tipo `AbstractArray`. El parámetro `N` es la dimensionalidad, que puede ser útil para tipos de AbstractArray que solo admiten dimensionalidades específicas:

```
struct SparseMatrixStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatrixStyle()
```

Para tipos `AbstractArray` que admiten dimensionalidad arbitraria, `N` se puede establecer en `Any`:

```
struct MyArrayStyle <: Broadcast.AbstractArrayStyle{Any} end
Base.BroadcastStyle(::Type{<:MyArray}) = MyArrayStyle()
```

En casos donde desees poder mezclar múltiples `AbstractArrayStyle`s y hacer un seguimiento de la dimensionalidad, tu estilo necesita admitir un constructor [`Val`](@ref):

```
struct MyArrayStyleDim{N} <: Broadcast.AbstractArrayStyle{N} end
(::Type{<:MyArrayStyleDim})(::Val{N}) where N = MyArrayStyleDim{N}()
```

Ten en cuenta que si dos o más subtipos de `AbstractArrayStyle` entran en conflicto, la maquinaria de broadcasting volverá a producir `Array`s. Si esto no es deseable, es posible que necesites definir reglas binarias [`BroadcastStyle`](@ref) para controlar el tipo de salida.

Consulta también [`Broadcast.DefaultArrayStyle`](@ref).
