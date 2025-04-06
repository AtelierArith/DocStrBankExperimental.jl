```
foldr(op, itr; [init])
```

[`reduce`](@ref) ile benzer, ancak sağdan birleştirme garantisi vardır. Sağlanan `init` anahtar kelime argümanı tam olarak bir kez kullanılacaktır. Genel olarak, boş koleksiyonlarla çalışmak için `init` sağlamak gerekecektir.

# Örnekler

```jldoctest
julia> foldr(=>, 1:4)
1 => (2 => (3 => 4))

julia> foldr(=>, 1:4; init=0)
1 => (2 => (3 => (4 => 0)))
```
