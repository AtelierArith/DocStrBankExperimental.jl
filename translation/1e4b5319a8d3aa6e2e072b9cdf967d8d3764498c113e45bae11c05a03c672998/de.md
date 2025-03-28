```
Union{}
```

`Union{}`, der leere [`Union`](@ref) von Typen, ist der Typ, der keine Werte hat. Das heißt, es hat die definierende Eigenschaft `isa(x, Union{}) == false` für jedes `x`. `Base.Bottom` ist als sein Alias definiert und der Typ von `Union{}` ist `Core.TypeofBottom`.

# Beispiele

```jldoctest
julia> isa(nothing, Union{})
false
```
