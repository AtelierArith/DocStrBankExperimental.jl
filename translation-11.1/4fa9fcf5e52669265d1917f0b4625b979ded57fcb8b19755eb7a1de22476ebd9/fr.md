# Collections and Data Structures

## [Iteration](@id lib-collections-iteration)

L'itération séquentielle est implémentée par la fonction [`iterate`](@ref). La boucle `for` générale :

```julia
for i in iter   # or  "for i = iter"
    # body
end
```

est traduit en :

```julia
next = iterate(iter)
while next !== nothing
    (i, state) = next
    # body
    next = iterate(iter, state)
end
```

L'objet `state` peut être n'importe quoi et doit être choisi de manière appropriée pour chaque type d'itérable. Voir le [manual section on the iteration interface](@ref man-interface-iteration) pour plus de détails sur la définition d'un type d'itérable personnalisé.

```@docs
Base.iterate
Base.IteratorSize
Base.IteratorEltype
```

Entièrement mis en œuvre par :

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`Number`](@ref)
  * [`AbstractArray`](@ref)
  * [`BitSet`](@ref)
  * [`IdDict`](@ref)
  * [`Dict`](@ref)
  * [`WeakKeyDict`](@ref)
  * `ChaqueLigne`
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

Entièrement mis en œuvre par :

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

Entièrement mis en œuvre par :

  * [`Array`](@ref)
  * [`BitArray`](@ref)
  * [`AbstractArray`](@ref)
  * `SousTableau`

Partiellement mis en œuvre par :

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`AbstractString`](@ref)
  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)
  * [`NamedTuple`](@ref)

## Dictionaries

[`Dict`](@ref) est le dictionnaire standard. Son implémentation utilise [`hash`](@ref) comme fonction de hachage pour la clé, et [`isequal`](@ref) pour déterminer l'égalité. Définissez ces deux fonctions pour des types personnalisés afin de remplacer la façon dont ils sont stockés dans une table de hachage.

[`IdDict`](@ref) est une table de hachage spéciale où les clés sont toujours des identités d'objet.

[`WeakKeyDict`](@ref) est une implémentation de table de hachage où les clés sont des références faibles à des objets, et peuvent donc être collectées par le ramasse-miettes même lorsqu'elles sont référencées dans une table de hachage. Comme `Dict`, elle utilise `hash` pour le hachage et `isequal` pour l'égalité, contrairement à `Dict`, elle ne convertit pas les clés lors de l'insertion.

[`Dict`](@ref) peut être créé en passant des objets de paire construits avec `=>` à un constructeur `4d61726b646f776e2e436f64652822222c2022446963742229_40726566` : `Dict("A"=>1, "B"=>2)`. Cet appel tentera d'inférer des informations de type à partir des clés et des valeurs (c'est-à-dire que cet exemple crée un `Dict{String, Int64}`). Pour spécifier explicitement les types, utilisez la syntaxe `Dict{KeyType,ValueType}(...)`. Par exemple, `Dict{String,Int32}("A"=>1, "B"=>2)`.

Les dictionnaires peuvent également être créés avec des générateurs. Par exemple, `Dict(i => f(i) for i = 1:10)`.

Étant donné un dictionnaire `D`, la syntaxe `D[x]` renvoie la valeur de la clé `x` (si elle existe) ou génère une erreur, et `D[x] = y` stocke la paire clé-valeur `x => y` dans `D` (remplaçant toute valeur existante pour la clé `x`). Plusieurs arguments pour `D[...]` sont convertis en tuples ; par exemple, la syntaxe `D[x,y]` est équivalente à `D[(x,y)]`, c'est-à-dire qu'elle fait référence à la valeur indexée par le tuple `(x,y)`.

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

Entièrement mis en œuvre par :

  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)

Partiellement mis en œuvre par :

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

Entièrement mis en œuvre par :

  * [`Set`](@ref)
  * [`BitSet`](@ref)
  * [`IdSet`](@ref)

Partiellement mis en œuvre par :

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

Entièrement mis en œuvre par :

  * `Vecteur` (a.k.a. 1-dimensionnel [`Array`](@ref))
  * `BitVector` (a.k.a. 1-dimensionnel [`BitArray`](@ref))

## Utility Collections

```@docs
Base.Pair
Iterators.Pairs
```
