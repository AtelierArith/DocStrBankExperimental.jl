```
repr(x; context=nothing)
```

Créez une chaîne à partir de n'importe quelle valeur en utilisant la fonction [`show`](@ref). Vous ne devez pas ajouter de méthodes à `repr`; définissez plutôt une méthode `show`.

L'argument clé optionnel `context` peut être défini comme une paire `:key=>value`, un tuple de paires `:key=>value`, ou un objet `IO` ou [`IOContext`](@ref) dont les attributs sont utilisés pour le flux I/O passé à `show`.

Notez que `repr(x)` est généralement similaire à la façon dont la valeur de `x` serait saisie en Julia. Voir aussi [`repr(MIME("text/plain"), x)`](@ref) pour retourner à la place une version "jolie" de `x` conçue davantage pour la consommation humaine, équivalente à l'affichage REPL de `x`.

!!! compat "Julia 1.7"
    Passer un tuple à l'argument clé `context` nécessite Julia 1.7 ou une version ultérieure.


# Exemples

```jldoctest
julia> repr(1)
"1"

julia> repr(zeros(3))
"[0.0, 0.0, 0.0]"

julia> repr(big(1/3))
"0.333333333333333314829616256247390992939472198486328125"

julia> repr(big(1/3), context=:compact => true)
"0.333333"
```
