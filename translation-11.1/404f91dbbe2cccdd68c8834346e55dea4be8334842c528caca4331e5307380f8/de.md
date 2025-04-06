```
applicable(f, args...) -> Bool
```

Bestimmen Sie, ob die gegebene generische Funktion eine Methode hat, die auf die gegebenen Argumente anwendbar ist.

Siehe auch [`hasmethod`](@ref).

# Beispiele

```jldoctest
julia> function f(x, y)
           x + y
       end;

julia> applicable(f, 1)
false

julia> applicable(f, 1, 2)
true
```
