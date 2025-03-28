```
LibGit2.StrArrayStruct
```

Une représentation de LibGit2 d'un tableau de chaînes de caractères. Correspond à la structure [`git_strarray`](https://libgit2.org/libgit2/#HEAD/type/git_strarray).

Lors de la récupération de données depuis LibGit2, une utilisation typique ressemblerait à :

```julia
sa_ref = Ref(StrArrayStruct())
@check ccall(..., (Ptr{StrArrayStruct},), sa_ref)
res = convert(Vector{String}, sa_ref[])
free(sa_ref)
```

En particulier, notez que `LibGit2.free` doit être appelé par la suite sur l'objet `Ref`.

Inversement, lors du passage d'un vecteur de chaînes de caractères à LibGit2, il est généralement plus simple de s'appuyer sur la conversion implicite :

```julia
strs = String[...]
@check ccall(..., (Ptr{StrArrayStruct},), strs)
```

Notez qu'aucun appel à `free` n'est requis car les données sont allouées par Julia.
