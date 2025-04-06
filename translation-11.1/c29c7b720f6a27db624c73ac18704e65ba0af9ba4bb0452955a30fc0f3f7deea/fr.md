```
GitBlame(repo::GitRepo, path::AbstractString; options::BlameOptions=BlameOptions())
```

Construit un objet `GitBlame` pour le fichier à `path`, en utilisant les informations de changement tirées de l'historique de `repo`. L'objet `GitBlame` enregistre qui a changé quels morceaux du fichier, quand et comment. `options` contrôle comment séparer le contenu du fichier et quels commits interroger - voir [`BlameOptions`](@ref) pour plus d'informations.
