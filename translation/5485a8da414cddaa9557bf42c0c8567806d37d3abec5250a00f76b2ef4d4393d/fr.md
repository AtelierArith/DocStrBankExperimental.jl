```
repr(mime, x; context=nothing)
```

Renvoie un `AbstractString` ou un `Vector{UInt8}` contenant la représentation de `x` dans le type `mime` demandé, comme écrit par [`show(io, mime, x)`](@ref) (générant une [`MethodError`](@ref) si aucune méthode `show` appropriée n'est disponible). Un `AbstractString` est renvoyé pour les types MIME avec des représentations textuelles (comme `"text/html"` ou `"application/postscript"`), tandis que les données binaires sont renvoyées sous forme de `Vector{UInt8}`. (La fonction `istextmime(mime)` renvoie si Julia traite un type `mime` donné comme texte.)

L'argument clé optionnel `context` peut être défini comme une paire `:key=>value` ou un objet `IO` ou [`IOContext`](@ref) dont les attributs sont utilisés pour le flux I/O passé à `show`.

Dans un cas particulier, si `x` est un `AbstractString` (pour les types MIME textuels) ou un `Vector{UInt8}` (pour les types MIME binaires), la fonction `repr` suppose que `x` est déjà au format `mime` demandé et renvoie simplement `x`. Ce cas particulier ne s'applique pas au type MIME `"text/plain"`. Cela est utile pour que des données brutes puissent être passées à `display(m::MIME, x)`.

En particulier, `repr("text/plain", x)` est généralement une version "bien formatée" de `x` conçue pour la consommation humaine. Voir aussi [`repr(x)`](@ref) pour renvoyer à la place une chaîne correspondant à [`show(x)`](@ref) qui pourrait être plus proche de la façon dont la valeur de `x` serait saisie dans Julia.

# Exemples

```jldoctest
julia> A = [1 2; 3 4];

julia> repr("text/plain", A)
"2×2 Matrix{Int64}:\n 1  2\n 3  4"
```
