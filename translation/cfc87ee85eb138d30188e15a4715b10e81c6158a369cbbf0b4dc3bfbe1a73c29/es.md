```
symlink(target::AbstractString, link::AbstractString; dir_target = false)
```

Crea un enlace simbólico a `target` con el nombre `link`.

En Windows, los enlaces simbólicos deben declararse explícitamente como referentes a un directorio o no. Si `target` ya existe, por defecto el tipo de `link` se detectará automáticamente; sin embargo, si `target` no existe, esta función por defecto crea un enlace simbólico de archivo a menos que `dir_target` se establezca en `true`. Ten en cuenta que si el usuario establece `dir_target` pero `target` existe y es un archivo, aún se creará un enlace simbólico de directorio, pero la desreferenciación del enlace simbólico fallará, justo como si el usuario crea un enlace simbólico de archivo (llamando a `symlink()` con `dir_target` establecido en `false` antes de que se cree el directorio) y trata de desreferenciarlo a un directorio.

Además, hay dos métodos para hacer un enlace en Windows; enlaces simbólicos y puntos de unión. Los puntos de unión son ligeramente más eficientes, pero no admiten rutas relativas, por lo que si se solicita un enlace simbólico de directorio relativo (como lo indica `isabspath(target)` devolviendo `false`), se utilizará un enlace simbólico, de lo contrario, se utilizará un punto de unión. La mejor práctica para crear enlaces simbólicos en Windows es crearlos solo después de que los archivos/directorios a los que hacen referencia ya estén creados.

Ver también: [`hardlink`](@ref).

!!! nota
    Esta función genera un error en sistemas operativos que no admiten enlaces simbólicos suaves, como Windows XP.


!!! compat "Julia 1.6"
    El argumento de palabra clave `dir_target` se agregó en Julia 1.6. Antes de esto, los enlaces simbólicos a rutas inexistentes en Windows siempre serían enlaces simbólicos de archivo, y los enlaces simbólicos relativos a directorios no eran compatibles.

