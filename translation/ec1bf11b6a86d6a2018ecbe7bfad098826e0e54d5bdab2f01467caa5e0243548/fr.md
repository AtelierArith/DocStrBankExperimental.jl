```
combine_styles(cs...) -> BroadcastStyle
```

Décide quel `BroadcastStyle` utiliser pour un nombre quelconque d'arguments de valeur. Utilise [`BroadcastStyle`](@ref) pour obtenir le style de chaque argument, et utilise [`result_style`](@ref) pour combiner les styles.

# Exemples

```jldoctest
julia> Broadcast.combine_styles([1], [1 2; 3 4])
Base.Broadcast.DefaultArrayStyle{2}()
```
