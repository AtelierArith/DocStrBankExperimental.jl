```
combine_styles(cs...) -> BroadcastStyle
```

Entscheidet, welchen `BroadcastStyle` für eine beliebige Anzahl von Wertargumenten verwendet werden soll. Verwendet [`BroadcastStyle`](@ref), um den Stil für jedes Argument zu erhalten, und verwendet [`result_style`](@ref), um Stile zu kombinieren.

# Beispiele

```jldoctest
julia> Broadcast.combine_styles([1], [1 2; 3 4])
Base.Broadcast.DefaultArrayStyle{2}()
```
