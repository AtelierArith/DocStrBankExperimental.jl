```
LibGit2.SignatureStruct
```

Une signature d'action (par exemple pour les committers, taggers, etc). Correspond à la structure [`git_signature`](https://libgit2.org/libgit2/#HEAD/type/git_signature).

Les champs représentent :

  * `name` : Le nom complet du committer ou de l'auteur du commit.
  * `email` : L'email auquel le committer/auteur peut être contacté.
  * `when` : une [`TimeStruct`](@ref) indiquant quand le commit a été créé/commité dans le dépôt.
