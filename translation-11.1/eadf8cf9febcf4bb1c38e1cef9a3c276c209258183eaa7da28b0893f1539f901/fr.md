```
Broadcast.broadcastable(x)
```

Retourne soit `x` soit un objet comme `x` tel qu'il supporte [`axes`](@ref), l'indexation, et son type supporte [`ndims`](@ref).

Si `x` supporte l'itération, la valeur retournée doit avoir les mêmes comportements d'`axes` et d'indexation que [`collect(x)`](@ref).

Si `x` n'est pas un `AbstractArray` mais qu'il supporte `axes`, l'indexation, et que son type supporte `ndims`, alors `broadcastable(::typeof(x))` peut être implémenté pour retourner simplement lui-même. De plus, si `x` définit son propre [`BroadcastStyle`](@ref), alors il doit définir sa méthode `broadcastable` pour retourner lui-même afin que le style personnalisé ait un effet.

# Exemples

```jldoctest
julia> Broadcast.broadcastable([1,2,3]) # comme `identity` puisque les tableaux supportent déjà axes et indexation
3-element Vector{Int64}:
 1
 2
 3

julia> Broadcast.broadcastable(Int) # Les types ne supportent pas axes, indexation, ou itération mais sont couramment utilisés comme scalaires
Base.RefValue{Type{Int64}}(Int64)

julia> Broadcast.broadcastable("hello") # Les chaînes rompent la convention de correspondance d'itération et agissent comme un scalaire à la place
Base.RefValue{String}("hello")
```
