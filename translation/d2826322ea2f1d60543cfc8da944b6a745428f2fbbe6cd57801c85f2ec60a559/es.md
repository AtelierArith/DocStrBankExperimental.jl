```
LibGit2.StrArrayStruct
```

Una representación de LibGit2 de un array de cadenas. Coincide con la estructura [`git_strarray`](https://libgit2.org/libgit2/#HEAD/type/git_strarray).

Al obtener datos de LibGit2, un uso típico se vería así:

```julia
sa_ref = Ref(StrArrayStruct())
@check ccall(..., (Ptr{StrArrayStruct},), sa_ref)
res = convert(Vector{String}, sa_ref[])
free(sa_ref)
```

En particular, tenga en cuenta que `LibGit2.free` debe ser llamado después sobre el objeto `Ref`.

Por el contrario, al pasar un vector de cadenas a LibGit2, generalmente es más sencillo confiar en la conversión implícita:

```julia
strs = String[...]
@check ccall(..., (Ptr{StrArrayStruct},), strs)
```

Tenga en cuenta que no se requiere ninguna llamada a `free` ya que los datos son asignados por Julia.
