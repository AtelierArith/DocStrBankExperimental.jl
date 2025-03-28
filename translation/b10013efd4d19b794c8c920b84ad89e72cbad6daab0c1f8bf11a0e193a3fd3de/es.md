```
Cmd(cmd::Cmd; ignorestatus, detach, windows_verbatim, windows_hide, env, dir)
Cmd(exec::Vector{String})
```

Construye un nuevo objeto `Cmd`, que representa un programa externo y argumentos, a partir de `cmd`, mientras cambia la configuración de los argumentos opcionales:

  * `ignorestatus::Bool`: Si es `true` (por defecto es `false`), entonces el `Cmd` no lanzará un error si el código de retorno es diferente de cero.
  * `detach::Bool`: Si es `true` (por defecto es `false`), entonces el `Cmd` se ejecutará en un nuevo grupo de procesos, permitiendo que sobreviva al proceso `julia` y que no se le pase Ctrl-C.
  * `windows_verbatim::Bool`: Si es `true` (por defecto es `false`), entonces en Windows el `Cmd` enviará una cadena de línea de comandos al proceso sin comillas ni escape de argumentos, incluso argumentos que contengan espacios. (En Windows, los argumentos se envían a un programa como una única cadena de "línea de comandos", y los programas son responsables de analizarla en argumentos. Por defecto, los argumentos vacíos y los argumentos con espacios o tabulaciones se citan con comillas dobles `"` en la línea de comandos, y `\` o `"` son precedidos por barras invertidas. `windows_verbatim=true` es útil para lanzar programas que analizan su línea de comandos de maneras no estándar.) No tiene efecto en sistemas que no son Windows.
  * `windows_hide::Bool`: Si es `true` (por defecto es `false`), entonces en Windows no se muestra una nueva ventana de consola cuando se ejecuta el `Cmd`. Esto no tiene efecto si ya hay una consola abierta o en sistemas que no son Windows.
  * `env`: Establece las variables de entorno a utilizar al ejecutar el `Cmd`. `env` es un diccionario que mapea cadenas a cadenas, un array de cadenas de la forma `"var=val"`, un array o tupla de pares `"var"=>val`. Para modificar (en lugar de reemplazar) el entorno existente, inicializa `env` con `copy(ENV)` y luego establece `env["var"]=val` según sea necesario. Para agregar a un bloque de entorno dentro de un objeto `Cmd` sin reemplazar todos los elementos, usa [`addenv()`](@ref) que devolverá un objeto `Cmd` con el entorno actualizado.
  * `dir::AbstractString`: Especifica un directorio de trabajo para el comando (en lugar del directorio actual).

Para cualquier palabra clave que no esté especificada, se utilizan las configuraciones actuales de `cmd`.

Ten en cuenta que el constructor `Cmd(exec)` no crea una copia de `exec`. Cualquier cambio posterior en `exec` se reflejará en el objeto `Cmd`.

La forma más común de construir un objeto `Cmd` es con literales de comando (comillas invertidas), por ejemplo:

```
`ls -l`
```

Esto se puede pasar al constructor `Cmd` para modificar su configuración, por ejemplo:

```
Cmd(`echo "Hello world"`, ignorestatus=true, detach=false)
```
