```
GitAnnotated(repo::GitRepo, commit_id::GitHash)
GitAnnotated(repo::GitRepo, ref::GitReference)
GitAnnotated(repo::GitRepo, fh::FetchHead)
GitAnnotated(repo::GitRepo, committish::AbstractString)
```

Un commit git anotado lleva consigo información sobre cómo fue buscado y por qué, de modo que las operaciones de rebase o merge tengan más información sobre el contexto del commit. Los archivos de conflicto contienen información sobre las ramas de origen/destino en el merge que están en conflicto, por ejemplo. Un commit anotado puede referirse a la punta de una rama remota, por ejemplo, cuando se pasa un [`FetchHead`](@ref), o a una cabeza de rama descrita usando `GitReference`.
