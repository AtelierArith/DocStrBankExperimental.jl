```
LibGit2.Buffer
```

Un búfer de datos para exportar datos de libgit2. Coincide con la estructura [`git_buf`](https://libgit2.org/libgit2/#HEAD/type/git_buf).

Al obtener datos de LibGit2, un uso típico se vería así:

```julia
buf_ref = Ref(Buffer())
@check ccall(..., (Ptr{Buffer},), buf_ref)
# operación sobre buf_ref
free(buf_ref)
```

En particular, tenga en cuenta que `LibGit2.free` debe ser llamado después sobre el objeto `Ref`.
