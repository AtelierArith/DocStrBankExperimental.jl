```
LibGit2.DiffDelta
```

Descripción de los cambios en una entrada. Coincide con la estructura [`git_diff_delta`](https://libgit2.org/libgit2/#HEAD/type/git_diff_delta).

Los campos representan:

  * `status`: Uno de `Consts.DELTA_STATUS`, que indica si el archivo ha sido agregado/modificado/eliminado.
  * `flags`: Banderas para el delta y los objetos en cada lado. Determina si tratar los archivos como binarios/texto, si existen en cada lado del diff, y si se sabe que los ids de los objetos son correctos.
  * `similarity`: Se utiliza para indicar si un archivo ha sido renombrado o copiado.
  * `nfiles`: El número de archivos en el delta (por ejemplo, si el delta se ejecutó en un id de commit de submódulo, puede contener más de un archivo).
  * `old_file`: Un [`DiffFile`](@ref) que contiene información sobre el/los archivo(s) antes de los cambios.
  * `new_file`: Un [`DiffFile`](@ref) que contiene información sobre el/los archivo(s) después de los cambios.
