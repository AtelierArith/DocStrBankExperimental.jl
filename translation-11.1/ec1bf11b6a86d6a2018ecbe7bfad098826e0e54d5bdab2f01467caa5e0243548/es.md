```
combine_styles(cs...) -> BroadcastStyle
```

Decide qué `BroadcastStyle` usar para cualquier número de argumentos de valor. Utiliza [`BroadcastStyle`](@ref) para obtener el estilo de cada argumento y usa [`result_style`](@ref) para combinar estilos.

# Ejemplos

```jldoctest
julia> Broadcast.combine_styles([1], [1 2; 3 4])
Base.Broadcast.DefaultArrayStyle{2}()
```
