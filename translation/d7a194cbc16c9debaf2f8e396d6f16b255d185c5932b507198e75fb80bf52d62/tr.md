```
collect(collection)
```

Bir koleksiyondan veya iteratörden tüm öğelerin bir `Array`'ini döndürür. Sözlükler için, `key=>value` [Pair](@ref Pair) çiftlerinin bir `Vector`'ını döndürür. Argüman dizi benzeri veya [`HasShape`](@ref IteratorSize) özelliğine sahip bir iteratör ise, sonuç argümanla aynı şekle ve boyut sayısına sahip olacaktır.

[Comprehensions](@ref man-comprehensions) tarafından bir [generator expression](@ref man-generators) 'ı bir `Array`'e dönüştürmek için kullanılır. Bu nedenle, *generator'lar üzerinde*, `collect` çağırmak yerine köşeli parantez notasyonu kullanılabilir, ikinci örneğe bakın.

# Örnekler

Bir `UnitRange{Int64}` koleksiyonundan öğeleri toplayın:

```jldoctest
julia> collect(1:3)
3-element Vector{Int64}:
 1
 2
 3
```

Bir generator'dan öğeleri toplayın (aynı çıktı `[x^2 for x in 1:3]` ile):

```jldoctest
julia> collect(x^2 for x in 1:3)
3-element Vector{Int64}:
 1
 4
 9
```
