```
get!(f::Union{Function, Type}, collection, key)
```

Gibt den Wert zurück, der für den angegebenen Schlüssel gespeichert ist, oder wenn keine Zuordnung für den Schlüssel vorhanden ist, speichere `key => f()`, und gebe `f()` zurück.

Dies ist dazu gedacht, mit der `do`-Block-Syntax aufgerufen zu werden.

# Beispiele

```jldoctest
julia> squares = Dict{Int, Int}();

julia> function get_square!(d, i)
           get!(d, i) do
               i^2
           end
       end
get_square! (generic function with 1 method)

julia> get_square!(squares, 2)
4

julia> squares
Dict{Int64, Int64} mit 1 Eintrag:
  2 => 4
```
