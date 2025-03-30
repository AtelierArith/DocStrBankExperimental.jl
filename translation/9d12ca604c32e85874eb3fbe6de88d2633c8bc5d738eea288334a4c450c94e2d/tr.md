```
PersistentDict
```

`PersistentDict`, bir hash array mapped trie olarak uygulanmış bir sözlüktür ve kalıcılık gerektiğinde optimaldir; her işlem, önceki sözlükten ayrı yeni bir sözlük döndürür, ancak temel uygulama alan verimlidir ve birden fazla ayrı sözlük arasında depolama paylaşabilir.

!!! not
    Bir IdDict gibi davranır.


```julia
PersistentDict(KV::Pair)
```

# Örnekler

```jldoctest
julia> dict = Base.PersistentDict(:a=>1)
Base.PersistentDict{Symbol, Int64} with 1 entry:
  :a => 1

julia> dict2 = Base.delete(dict, :a)
Base.PersistentDict{Symbol, Int64}()

julia> dict3 = Base.PersistentDict(dict, :a=>2)
Base.PersistentDict{Symbol, Int64} with 1 entry:
  :a => 2
```
