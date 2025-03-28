```
clone(repo_url::AbstractString, repo_path::AbstractString; kwargs...)
```

Clone un dépôt distant situé à `repo_url` vers l'emplacement du système de fichiers local `repo_path`.

Les arguments de mot-clé sont :

  * `branch::AbstractString=""`: quelle branche du dépôt distant cloner, si ce n'est pas la branche par défaut du dépôt (généralement `master`).
  * `isbare::Bool=false`: si `true`, clone le dépôt distant en tant que dépôt nu, ce qui fera de `repo_path` lui-même le répertoire git au lieu de `repo_path/.git`. Cela signifie qu'un arbre de travail ne peut pas être extrait. Joue le rôle de l'argument de la CLI git `--bare`.
  * `remote_cb::Ptr{Cvoid}=C_NULL`: un rappel qui sera utilisé pour créer le dépôt distant avant qu'il ne soit cloné. Si `C_NULL` (la valeur par défaut), aucune tentative ne sera faite pour créer le dépôt distant - il sera supposé déjà exister.
  * `credentials::Creds=nothing`: fournit des identifiants et/ou des paramètres lors de l'authentification contre un dépôt privé.
  * `callbacks::Callbacks=Callbacks()`: rappels et charges utiles fournis par l'utilisateur.

Équivalent à `git clone [-b <branch>] [--bare] <repo_url> <repo_path>`.

# Exemples

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo1 = LibGit2.clone(repo_url, "test_path")
repo2 = LibGit2.clone(repo_url, "test_path", isbare=true)
julia_url = "https://github.com/JuliaLang/julia"
julia_repo = LibGit2.clone(julia_url, "julia_path", branch="release-0.6")
```
