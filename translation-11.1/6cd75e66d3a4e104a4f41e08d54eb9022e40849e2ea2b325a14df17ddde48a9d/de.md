```
rpad(s, n::Integer, p::Union{AbstractChar,AbstractString}=' ') -> String
```

Stringify `s` und fügen Sie den resultierenden String rechts mit `p` auf, um ihn `n` Zeichen (in [`textwidth`](@ref)) lang zu machen. Wenn `s` bereits `n` Zeichen lang ist, wird ein gleichwertiger String zurückgegeben. Standardmäßig mit Leerzeichen auffüllen.

# Beispiele

```jldoctest
julia> rpad("März", 20)
"März               "
```

!!! compat "Julia 1.7"
    In Julia 1.7 wurde diese Funktion geändert, um `textwidth` anstelle einer Rohzeichenanzahl (Codepunkt) zu verwenden.

