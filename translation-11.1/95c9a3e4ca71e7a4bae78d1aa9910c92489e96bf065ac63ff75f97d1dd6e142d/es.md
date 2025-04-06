```
define_editor(fn, pattern; wait=false)
```

Define un nuevo editor que coincida con `pattern` que se puede usar para abrir un archivo (posiblemente en un número de línea dado) usando `fn`.

El argumento `fn` es una función que determina cómo abrir un archivo con el editor dado. Debe tomar cuatro argumentos, de la siguiente manera:

  * `cmd` - un objeto de comando base para el editor
  * `path` - la ruta al archivo fuente que se va a abrir
  * `line` - el número de línea para abrir el editor
  * `column` - el número de columna para abrir el editor

Los editores que no pueden abrirse en una línea específica con un comando o en una columna específica pueden ignorar el argumento `line` y/o `column`. La devolución de llamada `fn` debe devolver un objeto `Cmd` apropiado para abrir un archivo o `nothing` para indicar que no pueden editar este archivo. Usa `nothing` para indicar que este editor no es apropiado para el entorno actual y se debe intentar con otro editor. Es posible agregar más ganchos de edición generales que no necesiten generar comandos externos al empujar una devolución de llamada directamente al vector `EDITOR_CALLBACKS`.

El argumento `pattern` es una cadena, expresión regular o un arreglo de cadenas y expresiones regulares. Para que se llame a `fn`, uno de los patrones debe coincidir con el valor de `EDITOR`, `VISUAL` o `JULIA_EDITOR`. Para cadenas, la cadena debe ser igual al [`basename`](@ref) de la primera palabra del comando del editor, con su extensión, si la hay, eliminada. Por ejemplo, "vi" no coincide con "vim -g" pero coincide con "/usr/bin/vi -m"; también coincide con `vi.exe`. Si `pattern` es una regex, se compara con todo el comando del editor como una cadena escapada por el shell. Un patrón de arreglo coincide si cualquiera de sus elementos coincide. Si varios editores coinciden, se utiliza el que se agregó más recientemente.

Por defecto, julia no espera a que el editor se cierre, ejecutándolo en segundo plano. Sin embargo, si el editor es basado en terminal, probablemente querrás establecer `wait=true` y julia esperará a que el editor se cierre antes de reanudar.

Si una de las variables de entorno del editor está configurada, pero ninguna entrada de editor coincide con ella, se invoca la entrada de editor predeterminada:

```
(cmd, path, line, column) -> `$cmd $path`
```

Ten en cuenta que muchos editores ya están definidos. Todos los siguientes comandos deberían funcionar ya:

  * emacs
  * emacsclient
  * vim
  * nvim
  * nano
  * micro
  * kak
  * helix
  * textmate
  * mate
  * kate
  * subl
  * atom
  * notepad++
  * Visual Studio Code
  * open
  * pycharm
  * bbedit

# Ejemplos

Lo siguiente define el uso de `emacs` basado en terminal:

```
define_editor(
    r"\bemacs\b.*\s(-nw|--no-window-system)\b", wait=true) do cmd, path, line
    `$cmd +$line $path`
end
```

!!! compat "Julia 1.4"
    `define_editor` fue introducido en Julia 1.4.

