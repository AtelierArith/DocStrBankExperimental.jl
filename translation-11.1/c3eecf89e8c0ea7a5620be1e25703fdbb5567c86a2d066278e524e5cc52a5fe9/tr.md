```
any(p, itr) -> Bool
```

`itr`'deki herhangi bir öğe için `p`'nin `true` döndürüp döndürmediğini belirleyin, `p`'nin `true` döndürdüğü `itr`'deki ilk öğe ile karşılaşıldığında `true` döndürerek (kısa devre). `false` için kısa devre yapmak için [`all`](@ref) kullanın.

Girdi [`missing`](@ref) değerleri içeriyorsa, tüm eksik olmayan değerler `false` ise (veya eşdeğer olarak, girdi `true` değeri içermiyorsa) `missing` döndürün, [üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic) izleyerek.

# Örnekler

```jldoctest
julia> any(i->(4<=i<=6), [3,5,7])
true

julia> any(i -> (println(i); i > 3), 1:10)
1
2
3
4
true

julia> any(i -> i > 0, [1, missing])
true

julia> any(i -> i > 0, [-1, missing])
missing

julia> any(i -> i > 0, [-1, 0])
false
```
