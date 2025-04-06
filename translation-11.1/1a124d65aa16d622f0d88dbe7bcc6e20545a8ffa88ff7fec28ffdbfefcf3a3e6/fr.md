```
reset(s::IO)
```

Réinitialise un flux `s` à une position marquée précédemment et supprime la marque. Retourne la position marquée précédemment. Lance une erreur si le flux n'est pas marqué.

Voir aussi [`mark`](@ref), [`unmark`](@ref), [`ismarked`](@ref).
