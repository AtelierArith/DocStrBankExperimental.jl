```
find_artifacts_toml(path::String)
```

Étant donné le chemin vers un fichier `.jl` (tel que celui retourné par `__source__.file` dans un contexte de macro), trouvez le `(Julia)Artifacts.toml` qui est contenu dans le projet contenant (s'il existe), sinon retournez `nothing`.

!!! compat "Julia 1.3"
    Cette fonction nécessite au moins Julia 1.3.

