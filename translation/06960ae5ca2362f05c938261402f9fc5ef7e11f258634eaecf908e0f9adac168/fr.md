```
setenv(command::Cmd, env; dir)
```

Définir des variables d'environnement à utiliser lors de l'exécution de la commande donnée. `env` est soit un dictionnaire mappant des chaînes à des chaînes, un tableau de chaînes de la forme `"var=val"`, ou zéro ou plusieurs arguments de paire `"var"=>val`. Pour modifier (plutôt que de remplacer) l'environnement existant, créez `env` via `copy(ENV)` puis définissez `env["var"]=val` comme désiré, ou utilisez [`addenv`](@ref).

L'argument clé `dir` peut être utilisé pour spécifier un répertoire de travail pour la commande. `dir` par défaut est le `dir` actuellement défini pour `command` (qui est le répertoire de travail actuel s'il n'est pas déjà spécifié).

Voir aussi [`Cmd`](@ref), [`addenv`](@ref), [`ENV`](@ref), [`pwd`](@ref).
