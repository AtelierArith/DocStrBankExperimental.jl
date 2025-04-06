```
committer(c::GitCommit)
```

Retourne la `Signature` du committer du commit `c`. Le committer est la personne qui a engagé les modifications initialement écrites par l'[`author`](@ref), mais il n'est pas nécessaire qu'il soit le même que l'`author`, par exemple, si l'`author` a envoyé un patch à un `committer` qui l'a engagé.
