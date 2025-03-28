```
LibGit2.Buffer
```

Un tampon de données pour exporter des données de libgit2. Correspond à la structure [`git_buf`](https://libgit2.org/libgit2/#HEAD/type/git_buf).

Lors de la récupération de données depuis LibGit2, une utilisation typique ressemblerait à :

```julia
buf_ref = Ref(Buffer())
@check ccall(..., (Ptr{Buffer},), buf_ref)
# opération sur buf_ref
free(buf_ref)
```

En particulier, notez que `LibGit2.free` doit être appelé par la suite sur l'objet `Ref`.
