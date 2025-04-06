```
all(p, itr) -> Bool
```

`itr`'deki tüm elemanlar için `p`'nin `true` döndürüp döndürmediğini belirleyin, `p`'nin `false` döndürdüğü ilk öğe ile karşılaşıldığında `false` döndürerek (kısa devre). `true` için kısa devre yapmak için [`any`](@ref) kullanın.

Girdi [`missing`](@ref) değerleri içeriyorsa, tüm eksik olmayan değerler `true` ise (veya eşdeğer olarak, girdi `false` değeri içermiyorsa) `missing` döndürün, [üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic) izleyerek.

# Örnekler

```jldoctest
julia> all(i->(4<=i<=6), [4,5,6])
true

julia> all(i -> (println(i); i < 3), 1:10)
1
2
3
false

julia> all(i -> i > 0, [1, missing])
missing

julia> all(i -> i > 0, [-1, missing])
false

julia> all(i -> i > 0, [1, 2])
true
```
