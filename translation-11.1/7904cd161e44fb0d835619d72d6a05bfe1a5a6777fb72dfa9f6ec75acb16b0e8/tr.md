```
isassigned(array, i) -> Bool
```

Verilen dizinin `i` indeksine karşılık gelen bir değere sahip olup olmadığını test eder. İndeks sınırların dışındaysa veya tanımsız bir referansa sahipse `false` döner.

# Örnekler

```jldoctest
julia> isassigned(rand(3, 3), 5)
true

julia> isassigned(rand(3, 3), 3 * 3 + 1)
false

julia> mutable struct Foo end

julia> v = similar(rand(3), Foo)
3-element Vector{Foo}:
 #undef
 #undef
 #undef

julia> isassigned(v, 1)
false
```
