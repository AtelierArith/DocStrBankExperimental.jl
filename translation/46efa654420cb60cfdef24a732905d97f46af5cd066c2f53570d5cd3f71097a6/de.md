```
splat(f)
```

Entspricht

```julia
    my_splat(f) = args->f(args...)
```

d.h. gegeben eine Funktion gibt es eine neue Funktion zurück, die ein Argument annimmt und es in die ursprüngliche Funktion splat. Dies ist nützlich als Adapter, um eine Funktion mit mehreren Argumenten in einem Kontext zu übergeben, der ein einzelnes Argument erwartet, aber ein Tupel als dieses einzelne Argument übergibt.

# Beispiele

```jldoctest
julia> map(splat(+), zip(1:3,4:6))
3-element Vector{Int64}:
 5
 7
 9

julia> my_add = splat(+)
splat(+)

julia> my_add((1,2,3))
6
```
