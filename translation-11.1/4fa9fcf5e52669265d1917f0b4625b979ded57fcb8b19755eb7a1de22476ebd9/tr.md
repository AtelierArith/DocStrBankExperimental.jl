# Collections and Data Structures

## [Iteration](@id lib-collections-iteration)

Sıralı yineleme, [`iterate`](@ref) fonksiyonu ile uygulanır. Genel `for` döngüsü:

```julia
for i in iter   # or  "for i = iter"
    # body
end
```

lütfen çevrilecek metni yapıştırın.

```julia
next = iterate(iter)
while next !== nothing
    (i, state) = next
    # body
    next = iterate(iter, state)
end
```

`state` nesnesi herhangi bir şey olabilir ve her iterable türü için uygun bir şekilde seçilmelidir. Özel bir iterable türü tanımlama hakkında daha fazla bilgi için [manual section on the iteration interface](@ref man-interface-iteration)'a bakın.

```@docs
Base.iterate
Base.IteratorSize
Base.IteratorEltype
```

Tamamıyla uygulanmıştır:

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`Number`](@ref)
  * [`AbstractArray`](@ref)
  * [`BitSet`](@ref)
  * [`IdDict`](@ref)
  * [`Dict`](@ref)
  * [`WeakKeyDict`](@ref)
  * `HerSatır`
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

Tamamıyla uygulanmıştır:

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

Tamamıyla uygulanmıştır:

  * [`Array`](@ref)
  * [`BitArray`](@ref)
  * [`AbstractArray`](@ref)
  * `Alt Dizi`

Kısmen uygulanmıştır:

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`AbstractString`](@ref)
  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)
  * [`NamedTuple`](@ref)

## Dictionaries

[`Dict`](@ref) standart sözlük. Uygulaması, anahtar için [`hash`](@ref) ve eşitliği belirlemek için [`isequal`](@ref) hash fonksiyonunu kullanır. Özel türler için bu iki fonksiyonu tanımlayarak, bir hash tablosunda nasıl saklandıklarını geçersiz kılın.

[`IdDict`](@ref) özel bir hash tablosudur; burada anahtarlar her zaman nesne kimlikleridir.

[`WeakKeyDict`](@ref) bir hash tablosu uygulamasıdır; anahtarlar nesnelere zayıf referanslar olduğundan, bir hash tablosunda referans gösterilse bile çöp toplayıcı tarafından toplanabilirler. `Dict` gibi, hashing için `hash` ve eşitlik için `isequal` kullanır, ancak `Dict`'ten farklı olarak, ekleme sırasında anahtarları dönüştürmez.

[`Dict`](@ref) çift nesneleri ile `=>` kullanarak oluşturulabilir ve bir `4d61726b646f776e2e436f64652822222c2022446963742229_40726566` yapıcısına geçirilebilir: `Dict("A"=>1, "B"=>2)`. Bu çağrı, anahtarlar ve değerlerden tür bilgilerini çıkarmaya çalışacaktır (yani bu örnek bir `Dict{String, Int64}` oluşturur). Türleri açıkça belirtmek için `Dict{KeyType,ValueType}(...)` sözdizimini kullanın. Örneğin, `Dict{String,Int32}("A"=>1, "B"=>2)`.

Sözlükler, jeneratörlerle de oluşturulabilir. Örneğin, `Dict(i => f(i) for i = 1:10)`.

Verilen bir sözlük `D` için `D[x]` sözdizimi, `x` anahtarının değerini döndürür (eğer varsa) veya bir hata fırlatır ve `D[x] = y` sözdizimi, `D` içinde `x => y` anahtar-değer çiftini saklar (varsa `x` anahtarı için mevcut olan değeri değiştirir). `D[...]` için birden fazla argüman, demetlere dönüştürülür; örneğin, `D[x,y]` sözdizimi `D[(x,y)]` ile eşdeğerdir, yani `(x,y)` demeti ile anahtarlanan değere atıfta bulunur.

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

Tamamıyla uygulanmıştır:

  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)

Kısmen uygulanmıştır:

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

Tamamıyla uygulanmıştır:

  * [`Set`](@ref)
  * [`BitSet`](@ref)
  * [`IdSet`](@ref)

Kısmen uygulanmıştır:

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

Tamamıyla uygulanmıştır:

  * `Vektör` (diğer adıyla 1 boyutlu [`Array`](@ref))
  * `BitVector` (diğer adıyla 1 boyutlu [`BitArray`](@ref))

## Utility Collections

```@docs
Base.Pair
Iterators.Pairs
```
