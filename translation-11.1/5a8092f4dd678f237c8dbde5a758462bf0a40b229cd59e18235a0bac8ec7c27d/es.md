```
LibGit2.MergeOptions
```

Coincide con la estructura [`git_merge_options`](https://libgit2.org/libgit2/#HEAD/type/git_merge_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `flags`: un `enum` para las banderas que describen el comportamiento de la fusión. Definido en [`git_merge_flag_t`](https://github.com/libgit2/libgit2/blob/HEAD/include/git2/merge.h#L95). El enum correspondiente en Julia es `GIT_MERGE` y tiene los valores:

      * `MERGE_FIND_RENAMES`: detectar si un archivo ha sido renombrado entre el ancestro común y el lado "nuestro" o "suyo" de la fusión. Permite fusiones donde un archivo ha sido renombrado.
      * `MERGE_FAIL_ON_CONFLICT`: salir inmediatamente si se encuentra un conflicto en lugar de intentar resolverlo.
      * `MERGE_SKIP_REUC`: no escribir la extensión REUC en el índice resultante de la fusión.
      * `MERGE_NO_RECURSIVE`: si los commits que se están fusionando tienen múltiples bases de fusión, usar la primera, en lugar de intentar fusionar recursivamente las bases.
  * `rename_threshold`: cuán similares deben ser dos archivos para considerar uno como un renombramiento del otro. Este es un entero que establece el porcentaje de similitud. El valor predeterminado es 50.
  * `target_limit`: el número máximo de archivos con los que comparar para buscar renombramientos. El valor predeterminado es 200.
  * `metric`: función personalizada opcional para usar para determinar la similitud entre dos archivos para la detección de renombramientos.
  * `recursion_limit`: el límite superior en el número de fusiones de ancestros comunes a realizar para intentar construir una nueva base de fusión virtual para la fusión. El valor predeterminado es sin límite. Este campo solo está presente en versiones de libgit2 más nuevas que 0.24.0.
  * `default_driver`: el controlador de fusión a utilizar si ambos lados han cambiado. Este campo solo está presente en versiones de libgit2 más nuevas que 0.25.0.
  * `file_favor`: cómo manejar los contenidos de archivos en conflicto para el controlador `text`.

      * `MERGE_FILE_FAVOR_NORMAL`: si ambos lados de la fusión tienen cambios en una sección, hacer una nota del conflicto en el índice que `git checkout` usará para crear un archivo de fusión, que el usuario puede luego referenciar para resolver los conflictos. Este es el valor predeterminado.
      * `MERGE_FILE_FAVOR_OURS`: si ambos lados de la fusión tienen cambios en una sección, usar la versión en el lado "nuestro" de la fusión en el índice.
      * `MERGE_FILE_FAVOR_THEIRS`: si ambos lados de la fusión tienen cambios en una sección, usar la versión en el lado "suyo" de la fusión en el índice.
      * `MERGE_FILE_FAVOR_UNION`: si ambos lados de la fusión tienen cambios en una sección, incluir cada línea única de ambos lados en el archivo que se coloca en el índice.
  * `file_flags`: pautas para fusionar archivos.
