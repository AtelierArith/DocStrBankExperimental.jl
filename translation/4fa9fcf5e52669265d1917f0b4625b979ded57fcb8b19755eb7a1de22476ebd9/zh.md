# Collections and Data Structures

## [Iteration](@id lib-collections-iteration)

顺序迭代是通过 [`iterate`](@ref) 函数实现的。一般的 `for` 循环：

```julia
for i in iter   # or  "for i = iter"
    # body
end
```

请提供您希望翻译的Markdown内容或文本。

```julia
next = iterate(iter)
while next !== nothing
    (i, state) = next
    # body
    next = iterate(iter, state)
end
```

`state` 对象可以是任何东西，并应根据每种可迭代类型适当选择。有关定义自定义可迭代类型的更多详细信息，请参见 [manual section on the iteration interface](@ref man-interface-iteration)。

```@docs
Base.iterate
Base.IteratorSize
Base.IteratorEltype
```

完全实现者：

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`Number`](@ref)
  * [`AbstractArray`](@ref)
  * [`BitSet`](@ref)
  * [`IdDict`](@ref)
  * [`Dict`](@ref)
  * [`WeakKeyDict`](@ref)
  * `每行`
  * [`AbstractString`](@ref)
  * [`Set`](@ref)
  * [`Pair`](@ref)
  * [`NamedTuple`](@ref)

## Constructors and Types

```@docs
Base.AbstractRange
Base.OrdinalRange
Base.AbstractUnitRange
Base.StepRange
Base.UnitRange
Base.LinRange
```

## General Collections

```@docs
Base.isempty
Base.isdone
Base.empty!
Base.length
Base.checked_length
```

完全实现者：

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`Number`](@ref)
  * [`AbstractArray`](@ref)
  * [`BitSet`](@ref)
  * [`IdDict`](@ref)
  * [`Dict`](@ref)
  * [`WeakKeyDict`](@ref)
  * [`AbstractString`](@ref)
  * [`Set`](@ref)
  * [`NamedTuple`](@ref)

## Iterable Collections

```@docs
Base.in
Base.:∉
Base.hasfastin
Base.eltype
Base.indexin
Base.unique
Base.unique!
Base.allunique
Base.allequal
Base.reduce(::Any, ::Any)
Base.reduce(::Any, ::AbstractArray)
Base.foldl(::Any, ::Any)
Base.foldr(::Any, ::Any)
Base.maximum
Base.maximum!
Base.minimum
Base.minimum!
Base.extrema
Base.extrema!
Base.argmax
Base.argmin
Base.findmax
Base.findmin
Base.findmax!
Base.findmin!
Base.sum
Base.sum!
Base.prod
Base.prod!
Base.any(::Any)
Base.any(::AbstractArray, ::Any)
Base.any!
Base.all(::Any)
Base.all(::AbstractArray, ::Any)
Base.all!
Base.count
Base.foreach
Base.map
Base.map!
Base.mapreduce(::Any, ::Any, ::Any)
Base.mapfoldl(::Any, ::Any, ::Any)
Base.mapfoldr(::Any, ::Any, ::Any)
Base.first
Base.last
Base.front
Base.tail
Base.step
Base.collect(::Any)
Base.collect(::Type, ::Any)
Base.filter
Base.filter!
Base.replace(::Any, ::Pair...)
Base.replace(::Base.Callable, ::Any)
Base.replace!
Base.rest
Base.split_rest
```

## Indexable Collections

```@docs
Base.getindex
Base.setindex!
Base.firstindex
Base.lastindex
```

完全实现者：

  * [`Array`](@ref)
  * [`BitArray`](@ref)
  * [`AbstractArray`](@ref)
  * `子数组`

部分实现者：

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`AbstractString`](@ref)
  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)
  * [`NamedTuple`](@ref)

## Dictionaries

[`Dict`](@ref) 是标准字典。它的实现使用 [`hash`](@ref) 作为键的哈希函数，使用 [`isequal`](@ref) 来确定相等性。为自定义类型定义这两个函数，以覆盖它们在哈希表中的存储方式。

[`IdDict`](@ref) 是一个特殊的哈希表，其中键始终是对象标识。

[`WeakKeyDict`](@ref) 是一个哈希表实现，其中键是对对象的弱引用，因此即使在哈希表中被引用，也可能被垃圾回收。与 `Dict` 类似，它使用 `hash` 进行哈希和 `isequal` 进行相等性检查，不同于 `Dict`，它在插入时不转换键。

[`Dict`](@ref) 可以通过将使用 `=>` 构造的对对象传递给 `4d61726b646f776e2e436f64652822222c2022446963742229_40726566` 构造函数来创建：`Dict("A"=>1, "B"=>2)`。此调用将尝试从键和值推断类型信息（即此示例创建一个 `Dict{String, Int64}`）。要显式指定类型，请使用语法 `Dict{KeyType,ValueType}(...)`。例如，`Dict{String,Int32}("A"=>1, "B"=>2)`。

字典也可以通过生成器创建。例如，`Dict(i => f(i) for i = 1:10)`。

给定一个字典 `D`，语法 `D[x]` 返回键 `x` 的值（如果存在）或抛出错误，而 `D[x] = y` 将键值对 `x => y` 存储在 `D` 中（替换键 `x` 的任何现有值）。对 `D[...]` 的多个参数会被转换为元组；例如，语法 `D[x,y]` 等价于 `D[(x,y)]`，即它指的是由元组 `(x,y)` 键入的值。

```@docs
Base.AbstractDict
Base.Dict
Base.IdDict
Base.WeakKeyDict
Base.ImmutableDict
Base.PersistentDict
Base.haskey
Base.get
Base.get!
Base.getkey
Base.delete!
Base.pop!(::Any, ::Any, ::Any)
Base.keys
Base.values
Base.pairs
Base.merge
Base.mergewith
Base.merge!
Base.mergewith!
Base.sizehint!
Base.keytype
Base.valtype
```

完全实现者：

  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)

部分实现者：

  * [`Set`](@ref)
  * [`BitSet`](@ref)
  * [`IdSet`](@ref)
  * [`EnvDict`](@ref Base.EnvDict)
  * [`Array`](@ref)
  * [`BitArray`](@ref)
  * [`ImmutableDict`](@ref Base.ImmutableDict)
  * [`PersistentDict`](@ref Base.PersistentDict)
  * [`Iterators.Pairs`](@ref)

## Set-Like Collections

```@docs
Base.AbstractSet
Base.Set
Base.BitSet
Base.IdSet
Base.union
Base.union!
Base.intersect
Base.setdiff
Base.setdiff!
Base.symdiff
Base.symdiff!
Base.intersect!
Base.issubset
Base.in!
Base.:⊈
Base.:⊊
Base.issetequal
Base.isdisjoint
```

完全实现者：

  * [`Set`](@ref)
  * [`BitSet`](@ref)
  * [`IdSet`](@ref)

部分实现者：

  * [`Array`](@ref)

## Dequeues

```@docs
Base.push!
Base.pop!
Base.popat!
Base.pushfirst!
Base.popfirst!
Base.insert!
Base.deleteat!
Base.keepat!
Base.splice!
Base.resize!
Base.append!
Base.prepend!
```

完全实现者：

  * `向量`（又称为 1 维 [`Array`](@ref)）
  * `BitVector`（又称为一维 [`BitArray`](@ref)）

## Utility Collections

```@docs
Base.Pair
Iterators.Pairs
```
