# [Getting Started](@id man-getting-started)

La instalación de Julia es sencilla, ya sea utilizando binarios precompilados o compilando desde el código fuente. Descarga e instala Julia siguiendo las instrucciones en [https://julialang.org/downloads/](https://julialang.org/downloads/).

Si vienes a Julia desde uno de los siguientes lenguajes, entonces deberías comenzar leyendo la sección sobre las diferencias notables de [MATLAB](@ref Noteworthy-differences-from-MATLAB), [R](@ref Noteworthy-differences-from-R), [Python](@ref Noteworthy-differences-from-Python), [C/C++](@ref Noteworthy-differences-from-C/C) o [Common Lisp](@ref Noteworthy-differences-from-Common-Lisp). Esto te ayudará a evitar algunos errores comunes, ya que Julia difiere de esos lenguajes en muchas formas sutiles.

La forma más fácil de aprender y experimentar con Julia es comenzando una sesión interactiva (también conocida como un bucle de lectura-evaluación-impresión o "REPL") haciendo doble clic en el ejecutable de Julia o ejecutando `julia` desde la línea de comandos:

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia> 1 + 2\n3\n\njulia> ans\n3\n```")
```

Para salir de la sesión interactiva, escribe `CTRL-D` (presiona la tecla Control/`^` junto con la tecla `d`), o escribe `exit()`. Cuando se ejecuta en modo interactivo, `julia` muestra un banner y solicita al usuario que ingrese datos. Una vez que el usuario ha ingresado una expresión completa, como `1 + 2`, y presiona enter, la sesión interactiva evalúa la expresión y muestra su valor. Si se ingresa una expresión en una sesión interactiva con un punto y coma al final, su valor no se muestra. La variable `ans` está vinculada al valor de la última expresión evaluada, ya sea que se muestre o no. La variable `ans` solo está vinculada en sesiones interactivas, no cuando el código de Julia se ejecuta de otras maneras.

Para evaluar expresiones escritas en un archivo fuente `file.jl`, escribe `include("file.jl")`.

Para ejecutar código en un archivo de manera no interactiva, puedes pasarlo como el primer argumento al comando `julia`:

```
$ julia script.jl
```

Puedes pasar argumentos adicionales a Julia y a tu programa `script.jl`. Una lista detallada de todas las opciones disponibles se puede encontrar en [Command-line Interface](@ref cli).

## Resources

Una lista curada de recursos de aprendizaje útiles para ayudar a los nuevos usuarios a comenzar se puede encontrar en la [learning](https://julialang.org/learning/) página del sitio web principal de Julia.

Puedes usar el REPL como un recurso de aprendizaje cambiando al modo de ayuda. Cambia al modo de ayuda presionando `?` en un prompt vacío de `julia>`, antes de escribir cualquier otra cosa. Escribir una palabra clave en el modo de ayuda buscará la documentación para ella, junto con ejemplos. De manera similar para la mayoría de las funciones u otros objetos que puedas encontrar.

```
help?> begin
search: begin disable_sigint reenable_sigint

  begin

  begin...end denotes a block of code.
```

Si ya conoces un poco de Julia, es posible que desees echar un vistazo a [Performance Tips](@ref man-performance-tips) y [Workflow Tips](@ref man-workflow-tips).
