```
f ∘ g
```

Composer des fonctions : c'est-à-dire que `(f ∘ g)(args...; kwargs...)` signifie `f(g(args...; kwargs...))`. Le symbole `∘` peut être saisi dans le REPL Julia (et la plupart des éditeurs, correctement configurés) en tapant `\circ<tab>`.

La composition de fonctions fonctionne également sous forme préfixe : `∘(f, g)` est la même chose que `f ∘ g`. La forme préfixe prend en charge la composition de plusieurs fonctions : `∘(f, g, h) = f ∘ g ∘ h` et le splatting `∘(fs...)` pour composer une collection itérable de fonctions. Le dernier argument de `∘` s'exécute en premier.

!!! compat "Julia 1.4"
    La composition de plusieurs fonctions nécessite au moins Julia 1.4.


!!! compat "Julia 1.5"
    La composition d'une seule fonction ∘(f) nécessite au moins Julia 1.5.


!!! compat "Julia 1.7"
    L'utilisation d'arguments de mot-clé nécessite au moins Julia 1.7.


# Exemples

```jldoctest
julia> map(uppercase∘first, ["apple", "banana", "carrot"])
3-element Vector{Char}:
 'A': ASCII/Unicode U+0041 (category Lu: Letter, uppercase)
 'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
 'C': ASCII/Unicode U+0043 (category Lu: Letter, uppercase)

julia> (==(6)∘length).(["apple", "banana", "carrot"])
3-element BitVector:
 0
 1
 1

julia> fs = [
           x -> 2x
           x -> x-1
           x -> x/2
           x -> x+1
       ];

julia> ∘(fs...)(3)
2.0
```

Voir aussi [`ComposedFunction`](@ref), [`!f::Function`](@ref).
