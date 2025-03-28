```
dlopen(libfile::AbstractString [, flags::Integer]; throw_error:Bool = true)
```

Carga una biblioteca compartida, devolviendo un identificador opaco.

La extensión dada por la constante `dlext` (`.so`, `.dll` o `.dylib`) se puede omitir de la cadena `libfile`, ya que se agrega automáticamente si es necesario. Si `libfile` no es un nombre de ruta absoluto, entonces se buscan las rutas en el array `DL_LOAD_PATH` para `libfile`, seguido de la ruta de carga del sistema.

El argumento opcional de flags es un OR a nivel de bits de cero o más de `RTLD_LOCAL`, `RTLD_GLOBAL`, `RTLD_LAZY`, `RTLD_NOW`, `RTLD_NODELETE`, `RTLD_NOLOAD`, `RTLD_DEEPBIND` y `RTLD_FIRST`. Estos se convierten en los flags correspondientes del comando dlopen de POSIX (y/o GNU libc y/o MacOS), si es posible, o se ignoran si la funcionalidad especificada no está disponible en la plataforma actual. Los flags predeterminados son específicos de la plataforma. En MacOS, los flags predeterminados de `dlopen` son `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL`, mientras que en otras plataformas los predeterminados son `RTLD_LAZY|RTLD_DEEPBIND|RTLD_LOCAL`. Un uso importante de estos flags es especificar un comportamiento no predeterminado para cuando el cargador de bibliotecas dinámicas vincula referencias de bibliotecas a símbolos exportados y si las referencias vinculadas se colocan en el ámbito local del proceso o en el ámbito global. Por ejemplo, `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL` permite que los símbolos de la biblioteca estén disponibles para su uso en otras bibliotecas compartidas, abordando situaciones donde hay dependencias entre bibliotecas compartidas.

Si no se puede encontrar la biblioteca, este método lanza un error, a menos que el argumento de palabra clave `throw_error` esté configurado en `false`, en cuyo caso este método devuelve `nothing`.

!!! note
    A partir de Julia 1.6, este método reemplaza las rutas que comienzan con `@executable_path/` con la ruta al ejecutable de Julia, permitiendo cargas de rutas relativas reubicables. En Julia 1.5 y versiones anteriores, esto solo funcionaba en macOS.

