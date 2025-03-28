```
lpad(s, n::Integer, p::Union{AbstractChar,AbstractString}=' ') -> String
```

Stringify `s` und fügen Sie den resultierenden String links mit `p` auf, um ihn `n` Zeichen lang (in [`textwidth`](@ref)) zu machen. Wenn `s` bereits `n` Zeichen lang ist, wird ein gleichwertiger String zurückgegeben. Standardmäßig mit Leerzeichen auffüllen.

# Beispiele

```jldoctest
julia> lpad("März", 10)
"     März"
```

!!! compat "Julia 1.7"
    In Julia 1.7 wurde diese Funktion geändert, um `textwidth` anstelle einer Rohzeichenzählung (Codepunkt) zu verwenden.

