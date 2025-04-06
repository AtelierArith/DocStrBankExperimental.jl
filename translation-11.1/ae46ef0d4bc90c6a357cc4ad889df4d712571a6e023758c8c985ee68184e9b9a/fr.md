```
macro artifact_str(name)
```

Renvoie le chemin sur disque vers un artefact. Recherche automatiquement l'artefact par nom dans le fichier `(Julia)Artifacts.toml` du projet. Lance une erreur si l'artefact demandé n'est pas présent. S'il est exécuté dans le REPL, recherche le fichier toml en commençant par le répertoire actuel, voir `find_artifacts_toml()` pour plus de détails.

Si l'artefact est marqué "lazy" et que le package a `using LazyArtifacts` défini, l'artefact sera téléchargé à la demande avec `Pkg` la première fois que cette macro essaie de calculer le chemin. Les fichiers seront ensuite laissés installés localement pour plus tard.

Si `name` contient une barre oblique avant ou arrière, tous les éléments après la première barre oblique seront considérés comme des noms de chemin indexant dans l'artefact, permettant une ligne simple pour accéder à un seul fichier/répertoire au sein d'un artefact. Exemple :

```
ffmpeg_path = @artifact"FFMPEG/bin/ffmpeg"
```

!!! compat "Julia 1.3"
    Cette macro nécessite au moins Julia 1.3.


!!! compat "Julia 1.6"
    L'indexation par barre oblique nécessite au moins Julia 1.6.

