```
LibGit2.RebaseOperation
```

Describe una única instrucción/operación que se debe realizar durante el rebase. Coincide con la estructura [`git_rebase_operation`](https://libgit2.org/libgit2/#HEAD/type/git_rebase_operation_t).

Los campos representan:

  * `optype`: el tipo de operación de rebase que se está realizando actualmente. Las opciones son:

      * `REBASE_OPERATION_PICK`: cherry-pick el commit en cuestión.
      * `REBASE_OPERATION_REWORD`: cherry-pick el commit en cuestión, pero reescribir su mensaje utilizando el aviso.
      * `REBASE_OPERATION_EDIT`: cherry-pick el commit en cuestión, pero permitir que el usuario edite el contenido del commit y su mensaje.
      * `REBASE_OPERATION_SQUASH`: aplastar el commit en cuestión en el commit anterior. Los mensajes de los dos commits se fusionarán.
      * `REBASE_OPERATION_FIXUP`: aplastar el commit en cuestión en el commit anterior. Solo se utilizará el mensaje del commit anterior.
      * `REBASE_OPERATION_EXEC`: no cherry-pick un commit. Ejecutar un comando y continuar si el comando se ejecuta con éxito.
  * `id`: el [`GitHash`](@ref) del commit en el que se está trabajando durante este paso de rebase.
  * `exec`: en caso de que se use `REBASE_OPERATION_EXEC`, el comando a ejecutar durante este paso (por ejemplo, ejecutar la suite de pruebas después de cada commit).
