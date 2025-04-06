```
unique(f, itr)
```

Gibt ein Array zurück, das einen Wert aus `itr` für jeden einzigartigen Wert enthält, der durch die Anwendung von `f` auf die Elemente von `itr` erzeugt wird.

# Beispiele

```jldoctest
julia> unique(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4
```

Diese Funktionalität kann auch verwendet werden, um die *Indizes* der ersten Vorkommen einzigartiger Elemente in einem Array zu extrahieren:

```jldoctest
julia> a = [3.1, 4.2, 5.3, 3.1, 3.1, 3.1, 4.2, 1.7];

julia> i = unique(i -> a[i], eachindex(a))
4-element Vector{Int64}:
 1
 2
 3
 8

julia> a[i]
4-element Vector{Float64}:
 3.1
 4.2
 5.3
 1.7

julia> a[i] == unique(a)
true
```
