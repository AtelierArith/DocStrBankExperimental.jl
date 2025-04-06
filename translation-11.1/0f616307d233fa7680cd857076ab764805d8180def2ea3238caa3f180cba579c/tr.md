```
max(x, y, ...)
```

Argümanların maksimumunu [`isless`](@ref) ile karşılaştırarak döndürür. Argümanlardan herhangi biri [`missing`](@ref) ise, `missing` döner. Bir koleksiyondan maksimum elemanı almak için [`maximum`](@ref) fonksiyonuna da bakın.

# Örnekler

```jldoctest
julia> max(2, 5, 1)
5

julia> max(5, missing, 6)
missing
```
