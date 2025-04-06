```
tempname(parent=tempdir(); cleanup=true) -> String
```

Genera una ruta de archivo temporal. Esta función solo devuelve una ruta; no se crea ningún archivo. La ruta es probable que sea única, pero esto no se puede garantizar debido a la muy remota posibilidad de que dos llamadas simultáneas a `tempname` generen el mismo nombre de archivo. El nombre está garantizado para diferir de todos los archivos que ya existen en el momento de la llamada a `tempname`.

Cuando se llama sin argumentos, el nombre temporal será una ruta absoluta a un nombre temporal en el directorio temporal del sistema según lo indicado por `tempdir()`. Si se proporciona un argumento de directorio `parent`, la ruta temporal estará en ese directorio en su lugar.

La opción `cleanup` controla si el proceso intenta eliminar la ruta devuelta automáticamente cuando el proceso sale. Tenga en cuenta que la función `tempname` no crea ningún archivo o directorio en la ubicación devuelta, por lo que no hay nada que limpiar a menos que cree un archivo o directorio allí. Si lo hace y `cleanup` es `true`, se eliminará al finalizar el proceso.

!!! compat "Julia 1.4"
    Los argumentos `parent` y `cleanup` se añadieron en 1.4. Antes de Julia 1.4, la ruta `tempname` nunca se limpiaría al finalizar el proceso.


!!! warning
    Esto puede llevar a agujeros de seguridad si otro proceso obtiene el mismo nombre de archivo y crea el archivo antes de que usted pueda hacerlo. Abra el archivo con `JL_O_EXCL` si esto es una preocupación. También se recomienda usar [`mktemp()`](@ref) en su lugar.

