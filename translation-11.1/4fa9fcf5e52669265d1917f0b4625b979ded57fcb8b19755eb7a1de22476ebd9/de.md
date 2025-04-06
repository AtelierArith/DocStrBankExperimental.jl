# Collections and Data Structures

## [Iteration](@id lib-collections-iteration)

Die sequenzielle Iteration wird durch die [`iterate`](@ref)-Funktion implementiert. Die allgemeine `for`-Schleife:

```julia
for i in iter   # or  "for i = iter"
    # body
end
```

ist übersetzt in:

```julia
next = iterate(iter)
while next !== nothing
    (i, state) = next
    # body
    next = iterate(iter, state)
end
```

Das `state`-Objekt kann alles sein und sollte für jeden iterierbaren Typ angemessen gewählt werden. Siehe die [manual section on the iteration interface](@ref man-interface-iteration) für weitere Details zur Definition eines benutzerdefinierten iterierbaren Typs.

```@docs
Base.iterate
Base.IteratorSize
Base.IteratorEltype
```

Vollständig implementiert von:

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`Number`](@ref)
  * [`AbstractArray`](@ref)
  * [`BitSet`](@ref)
  * [`IdDict`](@ref)
  * [`Dict`](@ref)
  * [`WeakKeyDict`](@ref)
  * `JedeZeile`
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

Vollständig implementiert von:

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

Vollständig implementiert von:

  * [`Array`](@ref)
  * [`BitArray`](@ref)
  * [`AbstractArray`](@ref)
  * `Teilarray`

Teilweise implementiert von:

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`AbstractString`](@ref)
  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)
  * [`NamedTuple`](@ref)

## Dictionaries

[`Dict`](@ref) ist das Standardwörterbuch. Seine Implementierung verwendet [`hash`](@ref) als Hash-Funktion für den Schlüssel und [`isequal`](@ref), um die Gleichheit zu bestimmen. Definieren Sie diese beiden Funktionen für benutzerdefinierte Typen, um zu überschreiben, wie sie in einer Hashtabelle gespeichert werden.

[`IdDict`](@ref) ist eine spezielle Hash-Tabelle, in der die Schlüssel immer Objektidentitäten sind.

[`WeakKeyDict`](@ref) ist eine Implementierung einer Hash-Tabelle, bei der die Schlüssel schwache Referenzen auf Objekte sind und daher auch dann garbage collected werden können, wenn sie in einer Hash-Tabelle referenziert werden. Ähnlich wie `Dict` verwendet es `hash` zum Hashing und `isequal` für die Gleichheit, im Gegensatz zu `Dict` konvertiert es jedoch die Schlüssel nicht bei der Einfügung.

[`Dict`](@ref) kann erstellt werden, indem Paarobjekte, die mit `=>` konstruiert wurden, an einen `4d61726b646f776e2e436f64652822222c2022446963742229_40726566`-Konstruktor übergeben werden: `Dict("A"=>1, "B"=>2)`. Dieser Aufruf versucht, Typinformationen aus den Schlüsseln und Werten abzuleiten (d.h. dieses Beispiel erstellt ein `Dict{String, Int64}`). Um Typen explizit anzugeben, verwenden Sie die Syntax `Dict{KeyType,ValueType}(...)`. Zum Beispiel, `Dict{String,Int32}("A"=>1, "B"=>2)`.

Wörterbücher können auch mit Generatoren erstellt werden. Zum Beispiel, `Dict(i => f(i) for i = 1:10)`.

Gegeben ein Wörterbuch `D` gibt die Syntax `D[x]` den Wert des Schlüssels `x` zurück (wenn er existiert) oder wirft einen Fehler, und `D[x] = y` speichert das Schlüssel-Wert-Paar `x => y` in `D` (ersetzt jeden vorhandenen Wert für den Schlüssel `x`). Mehrere Argumente für `D[...]` werden in Tupel umgewandelt; zum Beispiel ist die Syntax `D[x,y]` äquivalent zu `D[(x,y)]`, d.h. sie verweist auf den Wert, der durch das Tupel `(x,y)` gekennzeichnet ist.

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

Vollständig implementiert von:

  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)

Teilweise implementiert von:

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

Vollständig implementiert von:

  * [`Set`](@ref)
  * [`BitSet`](@ref)
  * [`IdSet`](@ref)

Teilweise implementiert von:

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

Vollständig implementiert von:

  * `Vector` (auch bekannt als 1-dimensionale [`Array`](@ref))
  * `BitVector` (auch bekannt als 1-dimensionale [`BitArray`](@ref))

## Utility Collections

```@docs
Base.Pair
Iterators.Pairs
```
