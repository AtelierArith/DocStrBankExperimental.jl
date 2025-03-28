```
Iterators.accumulate(f, itr; [init])
```

Gegeben eine 2-Argumente-Funktion `f` und einen Iterator `itr`, gibt einen neuen Iterator zurück, der `f` successiv auf den vorherigen Wert und das nächste Element von `itr` anwendet.

Dies ist effektiv eine faule Version von [`Base.accumulate`](@ref).

!!! compat "Julia 1.5"
    Das Schlüsselwort-Argument `init` wurde in Julia 1.5 hinzugefügt.


# Beispiele

```jldoctest
julia> a = Iterators.accumulate(+, [1,2,3,4]);

julia> foreach(println, a)
1
3
6
10

julia> b = Iterators.accumulate(/, (2, 5, 2, 5); init = 100);

julia> collect(b)
4-element Vector{Float64}:
 50.0
 10.0
  5.0
  1.0
```
