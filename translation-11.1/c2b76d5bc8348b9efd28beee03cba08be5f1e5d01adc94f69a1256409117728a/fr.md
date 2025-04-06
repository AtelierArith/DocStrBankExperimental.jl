```
Sys.username() -> String
```

Renvoie le nom d'utilisateur pour l'utilisateur actuel. Si le nom d'utilisateur ne peut pas être déterminé ou est vide, cette fonction génère une erreur.

Pour récupérer un nom d'utilisateur qui peut être remplacé via une variable d'environnement, par exemple, `USER`, envisagez d'utiliser

```julia
user = get(Sys.username, ENV, "USER")
```

!!! compat "Julia 1.11"
    Cette fonction nécessite au moins Julia 1.11.


Voir aussi [`homedir`](@ref).
