```
foreach(f, c...) -> Nichts
```

Rufen Sie die Funktion `f` für jedes Element des iterierbaren `c` auf. Bei mehreren iterierbaren Argumenten wird `f` elementweise aufgerufen, und die Iteration stoppt, wenn ein Iterator beendet ist.

`foreach` sollte anstelle von [`map`](@ref) verwendet werden, wenn die Ergebnisse von `f` nicht benötigt werden, zum Beispiel in `foreach(println, array)`.

# Beispiele

```jldoctest
julia> tri = 1:3:7; res = Int[];

julia> foreach(x -> push!(res, x^2), tri)

julia> res
3-element Vector{Int64}:
  1
 16
 49

julia> foreach((x, y) -> println(x, " mit ", y), tri, 'a':'z')
1 mit a
4 mit b
7 mit c
```
