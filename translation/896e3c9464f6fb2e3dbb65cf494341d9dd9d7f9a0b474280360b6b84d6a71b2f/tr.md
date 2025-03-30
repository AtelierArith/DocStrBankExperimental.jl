```
Stateful(itr)
```

Bu iterator sarmalayıcı hakkında düşünmenin birkaç farklı yolu vardır:

1. Bir iterator ve onun yineleme durumunun etrafında değiştirilebilir bir sarmalayıcı sağlar.
2. Bir iterator benzeri soyutlamayı `Channel` benzeri bir soyutlamaya dönüştürür.
3. Bir öğe üretildiğinde kendi dinlenme iteratoru haline gelmek için değişen bir iterator'dur.

`Stateful`, normal iterator arayüzünü sağlar. Diğer değiştirilebilir iteratorlar (örneğin, [`Base.Channel`](@ref)) gibi, yineleme erken durdurulursa (örneğin, bir [`break`](@ref) ile bir [`for`](@ref) döngüsünde), yineleme aynı iterator nesnesi üzerinden devam edilerek aynı yerden yeniden başlatılabilir (bu, değiştirilemez bir iteratorun başlangıçtan yeniden başlamasıyla karşılaştırıldığında).

# Örnekler

```jldoctest
julia> a = Iterators.Stateful("abcdef");

julia> isempty(a)
false

julia> popfirst!(a)
'a': ASCII/Unicode U+0061 (kategori Ll: Harf, küçük)

julia> collect(Iterators.take(a, 3))
3-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (kategori Ll: Harf, küçük)
 'c': ASCII/Unicode U+0063 (kategori Ll: Harf, küçük)
 'd': ASCII/Unicode U+0064 (kategori Ll: Harf, küçük)

julia> collect(a)
2-element Vector{Char}:
 'e': ASCII/Unicode U+0065 (kategori Ll: Harf, küçük)
 'f': ASCII/Unicode U+0066 (kategori Ll: Harf, küçük)

julia> Iterators.reset!(a); popfirst!(a)
'a': ASCII/Unicode U+0061 (kategori Ll: Harf, küçük)

julia> Iterators.reset!(a, "hello"); popfirst!(a)
'h': ASCII/Unicode U+0068 (kategori Ll: Harf, küçük)
```

```jldoctest
julia> a = Iterators.Stateful([1,1,1,2,3,4]);

julia> for x in a; x == 1 || break; end

julia> peek(a)
3

julia> sum(a) # Kalan öğeleri topla
7
```
