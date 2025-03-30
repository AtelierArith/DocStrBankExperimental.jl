```
min(x, y, ...)
```

Argümanların en küçüğünü [`isless`](@ref) ile karşılaştırarak döndürür. Argümanlardan herhangi biri [`missing`](@ref) ise, `missing` döner. Bir koleksiyondan en küçük öğeyi almak için [`minimum`](@ref) fonksiyonuna da bakın.

# Örnekler

```jldoctest
julia> min(2, 5, 1)
1

julia> min(4, missing, 6)
missing
```
