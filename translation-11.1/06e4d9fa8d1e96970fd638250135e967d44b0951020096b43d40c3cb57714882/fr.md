```
string(xs...)
```

Créez une chaîne à partir de n'importe quelle valeur en utilisant la fonction [`print`](@ref).

`string` ne doit généralement pas être défini directement. Au lieu de cela, définissez une méthode `print(io::IO, x::MyType)`. Si `string(x)` pour un certain type doit être très efficace, il peut être judicieux d'ajouter une méthode à `string` et de définir `print(io::IO, x::MyType) = print(io, string(x))` pour garantir que les fonctions sont cohérentes.

Voir aussi : [`String`](@ref), [`repr`](@ref), [`sprint`](@ref), [`show`](@ref @show).

# Exemples

```jldoctest
julia> string("a", 1, true)
"a1true"
```
