```
|>(x, f)
```

Infix-Operator, der die Funktion `f` auf das Argument `x` anwendet. Dies ermöglicht es, `f(g(x))` als `x |> g |> f` zu schreiben. Bei der Verwendung mit anonymen Funktionen sind normalerweise Klammern um die Definition erforderlich, um die beabsichtigte Kette zu erhalten.

# Beispiele

```jldoctest
julia> 4 |> inv
0.25

julia> [2, 3, 5] |> sum |> inv
0.1

julia> [0 1; 2 3] .|> (x -> x^2) |> sum
14
```
