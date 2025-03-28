```
commit(repo::GitRepo, msg::AbstractString; kwargs...) -> GitHash
```

Wrapper autour de [`git_commit_create`](https://libgit2.org/libgit2/#HEAD/group/commit/git_commit_create). Créez un commit dans le dépôt `repo`. `msg` est le message du commit. Retourne l'OID du nouveau commit.

Les arguments clés sont :

  * `refname::AbstractString=Consts.HEAD_FILE` : si non NULL, le nom de la référence à mettre à jour pour pointer vers le nouveau commit. Par exemple, `"HEAD"` mettra à jour la HEAD de la branche actuelle. Si la référence n'existe pas encore, elle sera créée.
  * `author::Signature = Signature(repo)` est une `Signature` contenant des informations sur la personne qui a créé le commit.
  * `committer::Signature = Signature(repo)` est une `Signature` contenant des informations sur la personne qui a engagé le commit dans le dépôt. Pas nécessairement la même que `author`, par exemple si `author` a envoyé un patch à `committer` qui l'a engagé.
  * `tree_id::GitHash = GitHash()` est un arbre git à utiliser pour créer le commit, montrant son ascendance et sa relation avec tout autre historique. `tree` doit appartenir à `repo`.
  * `parent_ids::Vector{GitHash}=GitHash[]` est une liste de commits par [`GitHash`](@ref) à utiliser comme commits parents pour le nouveau, et peut être vide. Un commit peut avoir plusieurs parents s'il s'agit d'un commit de fusion, par exemple.
