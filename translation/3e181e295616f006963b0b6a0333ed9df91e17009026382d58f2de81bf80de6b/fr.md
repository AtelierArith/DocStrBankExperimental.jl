```
arg_mkdir(f::Function, arg::AbstractString) -> arg
arg_mkdir(f::Function, arg::Nothing) -> mktempdir()
```

La fonction `arg_mkdir` prend `arg` qui doit être l'un des éléments suivants :

  * un chemin vers un répertoire vide déjà existant,
  * un chemin inexistant qui peut être créé en tant que répertoire, ou
  * `nothing` dans ce cas un répertoire temporaire est créé.

Dans tous les cas, le chemin vers le répertoire est retourné. Si une erreur se produit lors de `f(arg)`, le répertoire est retourné à son état d'origine : s'il existait déjà mais était vide, il sera vidé ; s'il n'existait pas, il sera supprimé.
