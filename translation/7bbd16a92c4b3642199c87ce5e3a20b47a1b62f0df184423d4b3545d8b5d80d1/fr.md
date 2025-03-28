```
sprint(f::Function, args...; context=nothing, sizehint=0)
```

Appelle la fonction donnée avec un flux d'E/S et les arguments supplémentaires fournis. Tout ce qui est écrit dans ce flux d'E/S est renvoyé sous forme de chaîne. `context` peut être un [`IOContext`](@ref) dont les propriétés seront utilisées, une `Pair` spécifiant une propriété et sa valeur, ou un tuple de `Pair` spécifiant plusieurs propriétés et leurs valeurs. `sizehint` suggère la capacité du tampon (en octets).

L'argument clé optionnel `context` peut être défini comme une paire `:key=>value`, un tuple de paires `:key=>value`, ou un objet `IO` ou [`IOContext`](@ref) dont les attributs sont utilisés pour le flux d'E/S passé à `f`. L'optionnel `sizehint` est une taille suggérée (en octets) à allouer pour le tampon utilisé pour écrire la chaîne.

!!! compat "Julia 1.7"
    Passer un tuple à l'argument clé `context` nécessite Julia 1.7 ou une version ultérieure.


# Exemples

```jldoctest
julia> sprint(show, 66.66666; context=:compact => true)
"66.6667"

julia> sprint(showerror, BoundsError([1], 100))
"BoundsError: attempt to access 1-element Vector{Int64} at index [100]"
```
