```
LibGit2.FetchHead
```

Contiene la información sobre HEAD durante una recuperación, incluyendo el nombre y la URL de la rama de la que se recuperó, el oid del HEAD y si el HEAD recuperado ha sido fusionado localmente.

Los campos representan:

  * `name`: El nombre en la base de datos de referencias local del head de recuperación, por ejemplo,  `"refs/heads/master"`.
  * `url`: La URL del head de recuperación.
  * `oid`: El [`GitHash`](@ref) de la punta del head de recuperación.
  * `ismerge`: Bandera booleana que indica si los cambios en el remoto han sido fusionados en la copia local o no. Si `true`, la copia local está actualizada con el head de recuperación remoto.
