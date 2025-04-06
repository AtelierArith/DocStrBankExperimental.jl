```
...
```

Der "Splat"-Operator, `...`, repräsentiert eine Sequenz von Argumenten. `...` kann in Funktionsdefinitionen verwendet werden, um anzuzeigen, dass die Funktion eine beliebige Anzahl von Argumenten akzeptiert. `...` kann auch verwendet werden, um eine Funktion auf eine Sequenz von Argumenten anzuwenden.

# Beispiele

```jldoctest
julia> add(xs...) = reduce(+, xs)
add (generische Funktion mit 1 Methode)

julia> add(1, 2, 3, 4, 5)
15

julia> add([1, 2, 3]...)
6

julia> add(7, 1:100..., 1000:1100...)
111107
```
