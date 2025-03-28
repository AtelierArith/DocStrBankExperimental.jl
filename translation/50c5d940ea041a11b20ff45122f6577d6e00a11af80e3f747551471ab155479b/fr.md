```
GitAnnotated(repo::GitRepo, commit_id::GitHash)
GitAnnotated(repo::GitRepo, ref::GitReference)
GitAnnotated(repo::GitRepo, fh::FetchHead)
GitAnnotated(repo::GitRepo, committish::AbstractString)
```

Un commit git annoté contient des informations sur la façon dont il a été recherché et pourquoi, de sorte que les opérations de rebase ou de fusion disposent de plus d'informations sur le contexte du commit. Les fichiers de conflit contiennent des informations sur les branches source/cible dans la fusion qui sont en conflit, par exemple. Un commit annoté peut faire référence à la pointe d'une branche distante, par exemple lorsqu'un [`FetchHead`](@ref) est passé, ou à un chef de branche décrit à l'aide de `GitReference`.
