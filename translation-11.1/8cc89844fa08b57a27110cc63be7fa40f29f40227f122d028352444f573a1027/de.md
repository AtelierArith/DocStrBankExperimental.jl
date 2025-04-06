```
hasmethod(f, t::Type{<:Tuple}[, kwnames]; world=get_world_counter()) -> Bool
```

Bestimmen Sie, ob die gegebene generische Funktion eine Methode hat, die mit dem gegebenen `Tuple` von Argumenttypen übereinstimmt, wobei die obere Grenze des Weltalters durch `world` angegeben wird.

Wenn ein Tuple von Namen der Schlüsselwortargumente `kwnames` bereitgestellt wird, wird auch überprüft, ob die Methode von `f`, die mit `t` übereinstimmt, die gegebenen Namen der Schlüsselwortargumente hat. Wenn die übereinstimmende Methode eine variable Anzahl von Schlüsselwortargumenten akzeptiert, z. B. mit `kwargs...`, werden alle in `kwnames` angegebenen Namen als gültig betrachtet. Andernfalls müssen die bereitgestellten Namen eine Teilmenge der Schlüsselwortargumente der Methode sein.

Siehe auch [`applicable`](@ref).

!!! compat "Julia 1.2"
    Die Angabe von Namen der Schlüsselwortargumente erfordert Julia 1.2 oder höher.


# Beispiele

```jldoctest
julia> hasmethod(length, Tuple{Array})
true

julia> f(; oranges=0) = oranges;

julia> hasmethod(f, Tuple{}, (:oranges,))
true

julia> hasmethod(f, Tuple{}, (:apples, :bananas))
false

julia> g(; xs...) = 4;

julia> hasmethod(g, Tuple{}, (:a, :b, :c, :d))  # g akzeptiert beliebige kwargs
true
```
