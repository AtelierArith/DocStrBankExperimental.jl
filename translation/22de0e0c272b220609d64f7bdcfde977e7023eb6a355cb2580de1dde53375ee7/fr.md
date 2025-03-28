```
restore(s::State, repo::GitRepo)
```

Restaurez un dépôt `repo` à un `État` `s` précédent, par exemple le HEAD d'une branche avant une tentative de fusion. `s` peut être généré en utilisant la fonction [`snapshot`](@ref).
