```
transact(f::Function, repo::GitRepo)
```

Appliquez la fonction `f` au dépôt git `repo`, en prenant un [`snapshot`](@ref) avant d'appliquer `f`. Si une erreur se produit dans `f`, `repo` sera restauré à son état de snapshot en utilisant [`restore`](@ref). L'erreur qui s'est produite sera relancée, mais l'état de `repo` ne sera pas corrompu.
