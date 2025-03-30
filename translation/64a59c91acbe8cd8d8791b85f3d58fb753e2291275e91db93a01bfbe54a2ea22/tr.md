```
foldl(op, itr; [init])
```

[`reduce`](@ref) ile benzer, ancak sol birleştirmenin garantisi vardır. Sağlanan takdirde, `init` anahtar kelime argümanı tam olarak bir kez kullanılacaktır. Genel olarak, boş koleksiyonlarla çalışmak için `init` sağlamanız gerekecektir.

Ayrıca bkz. [`mapfoldl`](@ref), [`foldr`](@ref), [`accumulate`](@ref).

# Örnekler

```jldoctest
julia> foldl(=>, 1:4)
((1 => 2) => 3) => 4

julia> foldl(=>, 1:4; init=0)
(((0 => 1) => 2) => 3) => 4

julia> accumulate(=>, (1,2,3,4))
(1, 1 => 2, (1 => 2) => 3, ((1 => 2) => 3) => 4)
```
