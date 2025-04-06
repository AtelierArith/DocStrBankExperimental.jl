```
L'opérateur "splat", `...`, représente une séquence d'arguments. `...` peut être utilisé dans les définitions de fonction, pour indiquer que la fonction accepte un nombre arbitraire d'arguments. `...` peut également être utilisé pour appliquer une fonction à une séquence d'arguments.

# Exemples

```

jldoctest julia> add(xs...) = reduce(+, xs) add (generic function with 1 method)

julia> add(1, 2, 3, 4, 5) 15

julia> add([1, 2, 3]...) 6

julia> add(7, 1:100..., 1000:1100...) 111107

```

```
