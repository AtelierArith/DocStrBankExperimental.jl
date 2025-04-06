```
LibGit2.SignatureStruct
```

Una firma de acción (por ejemplo, para quienes hacen commits, etiquetadores, etc.). Coincide con la estructura [`git_signature`](https://libgit2.org/libgit2/#HEAD/type/git_signature).

Los campos representan:

  * `name`: El nombre completo del autor o del que hace el commit.
  * `email`: El correo electrónico al que se puede contactar al autor/commitente.
  * `when`: una [`TimeStruct`](@ref) que indica cuándo se autoró/commitió el commit en el repositorio.
