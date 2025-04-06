`Broadcast.AbstractArrayStyle{N} <: BroadcastStyle` est le supertype abstrait pour tout style associé à un type `AbstractArray`. Le paramètre `N` est la dimensionnalité, ce qui peut être utile pour les types AbstractArray qui ne prennent en charge que des dimensionnalités spécifiques :

```
struct SparseMatrixStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatrixStyle()
```

Pour les types `AbstractArray` qui prennent en charge une dimensionnalité arbitraire, `N` peut être défini sur `Any` :

```
struct MyArrayStyle <: Broadcast.AbstractArrayStyle{Any} end
Base.BroadcastStyle(::Type{<:MyArray}) = MyArrayStyle()
```

Dans les cas où vous souhaitez pouvoir mélanger plusieurs `AbstractArrayStyle`s et suivre la dimensionnalité, votre style doit prendre en charge un constructeur [`Val`](@ref) :

```
struct MyArrayStyleDim{N} <: Broadcast.AbstractArrayStyle{N} end
(::Type{<:MyArrayStyleDim})(::Val{N}) where N = MyArrayStyleDim{N}()
```

Notez que si deux ou plusieurs sous-types `AbstractArrayStyle` entrent en conflit, le mécanisme de diffusion reviendra à produire des `Array`s. Si cela est indésirable, vous devrez peut-être définir des règles binaires [`BroadcastStyle`](@ref) pour contrôler le type de sortie.

Voir aussi [`Broadcast.DefaultArrayStyle`](@ref).
