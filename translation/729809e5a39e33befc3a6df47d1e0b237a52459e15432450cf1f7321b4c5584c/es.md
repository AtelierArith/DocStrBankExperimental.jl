```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/REPL/docs/src/index.md"
```

# The Julia REPL

Julia viene con un REPL (bucle de lectura-evaluación-impresión) interactivo y completo integrado en el ejecutable `julia`. Además de permitir la evaluación rápida y sencilla de las declaraciones de Julia, tiene un historial buscable, autocompletado, muchas combinaciones de teclas útiles y modos de ayuda y shell dedicados. El REPL se puede iniciar simplemente llamando a `julia` sin argumentos o haciendo doble clic en el ejecutable:

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia>\n```")
```

Para salir de la sesión interactiva, escribe `^D` – la tecla de control junto con la tecla `d` en una línea en blanco – o escribe `exit()` seguido de la tecla de retorno o enter. El REPL te saluda con un banner y un aviso `julia>`.

## The different prompt modes

### The Julian mode

El REPL tiene cinco modos principales de operación. El primero y más común es el aviso de Julia. Es el modo de operación predeterminado; cada nueva línea comienza inicialmente con `julia>`. Es aquí donde puedes ingresar expresiones de Julia. Presionar return o enter después de haber ingresado una expresión completa evaluará la entrada y mostrará el resultado de la última expresión.

```jldoctest
julia> string(1 + 2)
"3"
```

Hay una serie de características útiles únicas del trabajo interactivo. Además de mostrar el resultado, el REPL también vincula el resultado a la variable `ans`. Un punto y coma al final de la línea se puede usar como una bandera para suprimir la visualización del resultado.

```jldoctest
julia> string(3 * 4);

julia> ans
"12"
```

En el modo Julia, el REPL admite algo llamado *pegado de indicaciones*. Esto se activa al pegar texto que comienza con `julia>` en el REPL. En ese caso, solo se analizan las expresiones que comienzan con `julia>` (así como los otros indicadores de modo REPL: `shell>`, `help?>`, `pkg>`) y los demás se eliminan. Esto hace posible pegar un bloque de texto que ha sido copiado de una sesión REPL sin tener que eliminar las indicaciones y salidas. Esta función está habilitada por defecto, pero se puede deshabilitar o habilitar a voluntad con `REPL.enable_promptpaste(::Bool)`. Si está habilitada, puedes probarla pegando el bloque de código que está encima de este párrafo directamente en el REPL. Esta función no funciona en el símbolo del sistema estándar de Windows debido a su limitación para detectar cuándo ocurre un pegado.

Objects are printed at the REPL using the [`show`](@ref) function with a specific [`IOContext`](@ref). In particular, the `:limit` attribute is set to `true`. Other attributes can receive in certain `show` methods a default value if it's not already set, like `:compact`. It's possible, as an experimental feature, to specify the attributes used by the REPL via the `Base.active_repl.options.iocontext` dictionary (associating values to attributes). For example:

```julia-repl
julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.8833    0.329197
 0.719708  0.59114

julia> show(IOContext(stdout, :compact => false), "text/plain", rand(2, 2))
 0.43540323669187075  0.15759787870609387
 0.2540832269192739   0.4597637838786053
julia> Base.active_repl.options.iocontext[:compact] = false;

julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.2083967319174056  0.13330606013126012
 0.6244375177790158  0.9777957560761545
```

Para definir automáticamente los valores de este diccionario en el momento del inicio, se puede utilizar la función [`atreplinit`](@ref) en el archivo `~/.julia/config/startup.jl`, por ejemplo:

```julia
atreplinit() do repl
    repl.options.iocontext[:compact] = false
end
```

### Help mode

Cuando el cursor está al principio de la línea, el aviso se puede cambiar a un modo de ayuda escribiendo `?`. Julia intentará imprimir ayuda o documentación para cualquier cosa ingresada en el modo de ayuda:

```julia-repl
julia> ? # upon typing ?, the prompt changes (in place) to: help?>

help?> string
search: string String Cstring Cwstring RevString randstring bytestring SubString

  string(xs...)

  Create a string from any values using the print function.
```

Los macros, tipos y variables también se pueden consultar:

```
help?> @time
  @time

  A macro to execute an expression, printing the time it took to execute, the number of allocations,
  and the total number of bytes its execution caused to be allocated, before returning the value of the
  expression.

  See also @timev, @timed, @elapsed, and @allocated.

help?> Int32
search: Int32 UInt32

  Int32 <: Signed

  32-bit signed integer type.
```

Una cadena o literal de regex busca en todos los docstrings usando [`apropos`](@ref):

```
help?> "aprop"
REPL.stripmd
Base.Docs.apropos

help?> r"ap..p"
Base.:∘
Base.shell_escape_posixly
Distributed.CachingPool
REPL.stripmd
Base.Docs.apropos
```

Otra característica del modo de ayuda es la capacidad de acceder a docstrings extendidos. Puedes hacer esto escribiendo algo como `??Print` en lugar de `?Print`, lo que mostrará la sección `# Ayuda extendida` de la documentación del código fuente.

El modo de ayuda se puede salir presionando retroceso al principio de la línea.

### [Shell mode](@id man-shell-mode)

Así como el modo de ayuda es útil para acceder rápidamente a la documentación, otra tarea común es usar el shell del sistema para ejecutar comandos del sistema. Así como `?` ingresa al modo de ayuda cuando está al principio de la línea, un punto y coma (`;`) ingresará al modo de shell. Y se puede salir presionando retroceso al principio de la línea.

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> echo hello
hello
```

!!! note
    Para los usuarios de Windows, el modo shell de Julia no expone los comandos de shell de Windows. Por lo tanto, esto fallará:


```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> dir
ERROR: IOError: could not spawn `dir`: no such file or directory (ENOENT)
Stacktrace!
.......
```

Sin embargo, puedes acceder a `PowerShell` de esta manera:

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> powershell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.
PS C:\Users\elm>
```

... y a `cmd.exe` así (ver el comando `dir`):

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> cmd
Microsoft Windows [version 10.0.17763.973]
(c) 2018 Microsoft Corporation. All rights reserved.
C:\Users\elm>dir
 Volume in drive C has no label
 Volume Serial Number is 1643-0CD7
  Directory of C:\Users\elm

29/01/2020  22:15    <DIR>          .
29/01/2020  22:15    <DIR>          ..
02/02/2020  08:06    <DIR>          .atom
```

### Pkg mode

El modo del gestor de paquetes acepta comandos especializados para cargar y actualizar paquetes. Se ingresa presionando la tecla `]` en el aviso del REPL de Julian y se sale presionando CTRL-C o la tecla de retroceso al principio de la línea. El aviso para este modo es `pkg>`. Soporta su propio modo de ayuda, que se activa presionando `?` al principio de la línea del aviso `pkg>`. El modo del gestor de paquetes está documentado en el manual de Pkg, disponible en [https://julialang.github.io/Pkg.jl/v1/](https://julialang.github.io/Pkg.jl/v1/).

### Search modes

En todos los modos anteriores, las líneas ejecutadas se guardan en un archivo de historial, que se puede buscar. Para iniciar una búsqueda incremental a través del historial anterior, escribe `^R` – la tecla de control junto con la tecla `r`. El aviso cambiará a ```(reverse-i-search)`':```, y a medida que escribas, la consulta de búsqueda aparecerá entre comillas. El resultado más reciente que coincida con la consulta se actualizará dinámicamente a la derecha de los dos puntos a medida que se escriba más. Para encontrar un resultado más antiguo utilizando la misma consulta, simplemente escribe `^R` nuevamente.

Justo como `^R` es una búsqueda inversa, `^S` es una búsqueda hacia adelante, con el aviso ```(i-search)`':```. Los dos pueden usarse en conjunto para moverse a través de los resultados coincidentes anteriores o siguientes, respectivamente.

Todos los comandos ejecutados en el REPL de Julia se registran en `~/.julia/logs/repl_history.jl`, junto con una marca de tiempo de cuándo se ejecutaron y el modo actual del REPL en el que te encontrabas. El modo de búsqueda consulta este archivo de registro para encontrar los comandos que ejecutaste anteriormente. Esto se puede desactivar al inicio pasando la opción `--history-file=no` a Julia.

## Key bindings

El REPL de Julia hace un gran uso de los atajos de teclado. Varios atajos de control ya se introdujeron anteriormente (`^D` para salir, `^R` y `^S` para buscar), pero hay muchos más. Además de la tecla de control, también hay atajos de tecla meta. Estos varían más según la plataforma, pero la mayoría de las terminales por defecto utilizan alt- o option- mantenido junto con una tecla para enviar la tecla meta (o se pueden configurar para hacerlo), o presionando Esc y luego la tecla.

| Keybinding           | Description                                                                                                |
|:-------------------- |:---------------------------------------------------------------------------------------------------------- |
| **Program control**  |                                                                                                            |
| `^D`                 | Exit (when buffer is empty)                                                                                |
| `^C`                 | Interrupt or cancel                                                                                        |
| `^L`                 | Clear console screen                                                                                       |
| Return/Enter, `^J`   | New line, executing if it is complete                                                                      |
| meta-Return/Enter    | Insert new line without executing it                                                                       |
| `?` or `;`           | Enter help or shell mode (when at start of a line)                                                         |
| `^R`, `^S`           | Incremental history search, described above                                                                |
| **Cursor movement**  |                                                                                                            |
| Right arrow, `^F`    | Move right one character                                                                                   |
| Left arrow, `^B`     | Move left one character                                                                                    |
| ctrl-Right, `meta-F` | Move right one word                                                                                        |
| ctrl-Left, `meta-B`  | Move left one word                                                                                         |
| Home, `^A`           | Move to beginning of line                                                                                  |
| End, `^E`            | Move to end of line                                                                                        |
| Up arrow, `^P`       | Move up one line (or change to the previous history entry that matches the text before the cursor)         |
| Down arrow, `^N`     | Move down one line (or change to the next history entry that matches the text before the cursor)           |
| Shift-Arrow Key      | Move cursor according to the direction of the Arrow key, while activating the region ("shift selection")   |
| Page-up, `meta-P`    | Change to the previous history entry                                                                       |
| Page-down, `meta-N`  | Change to the next history entry                                                                           |
| `meta-<`             | Change to the first history entry (of the current session if it is before the current position in history) |
| `meta->`             | Change to the last history entry                                                                           |
| `^-Space`            | Set the "mark" in the editing region (and de-activate the region if it's active)                           |
| `^-Space ^-Space`    | Set the "mark" in the editing region and make the region "active", i.e. highlighted                        |
| `^G`                 | De-activate the region (i.e. make it not highlighted)                                                      |
| `^X^X`               | Exchange the current position with the mark                                                                |
| **Editing**          |                                                                                                            |
| Backspace, `^H`      | Delete the previous character, or the whole region when it's active                                        |
| Delete, `^D`         | Forward delete one character (when buffer has text)                                                        |
| meta-Backspace       | Delete the previous word                                                                                   |
| `meta-d`             | Forward delete the next word                                                                               |
| `^W`                 | Delete previous text up to the nearest whitespace                                                          |
| `meta-w`             | Copy the current region in the kill ring                                                                   |
| `meta-W`             | "Kill" the current region, placing the text in the kill ring                                               |
| `^U`                 | "Kill" to beginning of line, placing the text in the kill ring                                             |
| `^K`                 | "Kill" to end of line, placing the text in the kill ring                                                   |
| `^Y`                 | "Yank" insert the text from the kill ring                                                                  |
| `meta-y`             | Replace a previously yanked text with an older entry from the kill ring                                    |
| `^T`                 | Transpose the characters about the cursor                                                                  |
| `meta-Up arrow`      | Transpose current line with line above                                                                     |
| `meta-Down arrow`    | Transpose current line with line below                                                                     |
| `meta-u`             | Change the next word to uppercase                                                                          |
| `meta-c`             | Change the next word to titlecase                                                                          |
| `meta-l`             | Change the next word to lowercase                                                                          |
| `^/`, `^_`           | Undo previous editing action                                                                               |
| `^Q`                 | Write a number in REPL and press `^Q` to open editor at corresponding stackframe or method                 |
| `meta-Left Arrow`    | Indent the current line on the left                                                                        |
| `meta-Right Arrow`   | Indent the current line on the right                                                                       |
| `meta-.`             | Insert last word from previous history entry                                                               |
| `meta-e`             | Edit the current input in an editor                                                                        |

### Customizing keybindings

Las combinaciones de teclas del REPL de Julia se pueden personalizar completamente según las preferencias del usuario pasando un diccionario a `REPL.setup_interface`. Las claves de este diccionario pueden ser caracteres o cadenas. La clave `'*'` se refiere a la acción predeterminada. Las combinaciones de Control más el carácter `x` se indican con `"^x"`. Meta más `x` se puede escribir como `"\\M-x"` o `"\ex"`, y Control más `x` se puede escribir como `"\\C-x"` o `"^x"`. Los valores del mapa de teclas personalizado deben ser `nothing` (lo que indica que la entrada debe ser ignorada) o funciones que acepten la firma `(PromptState, AbstractREPL, Char)`. La función `REPL.setup_interface` debe ser llamada antes de que se inicialice el REPL, registrando la operación con [`atreplinit`](@ref). Por ejemplo, para vincular las teclas de flecha hacia arriba y hacia abajo para moverse a través del historial sin búsqueda de prefijo, se podría poner el siguiente código en `~/.julia/config/startup.jl`:

```julia
import REPL
import REPL.LineEdit

const mykeys = Dict{Any,Any}(
    # Up Arrow
    "\e[A" => (s,o...)->(LineEdit.edit_move_up(s) || LineEdit.history_prev(s, LineEdit.mode(s).hist)),
    # Down Arrow
    "\e[B" => (s,o...)->(LineEdit.edit_move_down(s) || LineEdit.history_next(s, LineEdit.mode(s).hist))
)

function customize_keys(repl)
    repl.interface = REPL.setup_interface(repl; extra_repl_keymap = mykeys)
end

atreplinit(customize_keys)
```

Los usuarios deben consultar `LineEdit.jl` para descubrir las acciones disponibles en la entrada de teclas.

## Tab completion

En los modos Julian, pkg y help del REPL, se puede ingresar los primeros caracteres de una función o tipo y luego presionar la tecla tab para obtener una lista de todas las coincidencias:

```julia-repl
julia> x[TAB]
julia> xor
```

En algunos casos, solo completa parte del nombre, hasta la siguiente ambigüedad:

```julia-repl
julia> mapf[TAB]
julia> mapfold
```

Si presionas tab de nuevo, obtendrás la lista de cosas que podrían completar esto:

```julia-repl
julia> mapfold[TAB]
mapfoldl mapfoldr
```

Cuando hay un solo resultado de autocompletado completo disponible al final de una línea de entrada y se han escrito 2 o más caracteres, se mostrará una pista de la finalización en un color más claro. Esto se puede desactivar mediante `Base.active_repl.options.hint_tab_completes = false`.

!!! compat "Julia 1.11"
    La sugerencia de autocompletado con tabulador se agregó en Julia 1.11.


Como otros componentes del REPL, la búsqueda distingue entre mayúsculas y minúsculas:

```julia-repl
julia> stri[TAB]
stride     strides     string      strip

julia> Stri[TAB]
StridedArray    StridedMatrix    StridedVecOrMat  StridedVector    String
```

La tecla de tabulación también se puede usar para sustituir los símbolos matemáticos de LaTeX por sus equivalentes en Unicode, y obtener una lista de coincidencias de LaTeX también:

```julia-repl
julia> \pi[TAB]
julia> π
π = 3.1415926535897...

julia> e\_1[TAB] = [1,0]
julia> e₁ = [1,0]
2-element Array{Int64,1}:
 1
 0

julia> e\^1[TAB] = [1 0]
julia> e¹ = [1 0]
1×2 Array{Int64,2}:
 1  0

julia> \sqrt[TAB]2     # √ is equivalent to the sqrt function
julia> √2
1.4142135623730951

julia> \hbar[TAB](h) = h / 2\pi[TAB]
julia> ħ(h) = h / 2π
ħ (generic function with 1 method)

julia> \h[TAB]
\hat              \hermitconjmatrix  \hkswarow          \hrectangle
\hatapprox        \hexagon           \hookleftarrow     \hrectangleblack
\hbar             \hexagonblack      \hookrightarrow    \hslash
\heartsuit        \hksearow          \house             \hspace

julia> α="\alpha[TAB]"   # LaTeX completion also works in strings
julia> α="α"
```

Una lista completa de las tabulaciones automáticas se puede encontrar en la sección [Unicode Input](@ref) del manual.

La finalización de rutas funciona para cadenas y el modo shell de Julia:

```julia-repl
julia> path="/[TAB]"
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
shell> /[TAB]
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
```

Las claves del diccionario también se pueden completar con tabulación:

```julia-repl
julia> foo = Dict("qwer1"=>1, "qwer2"=>2, "asdf"=>3)
Dict{String,Int64} with 3 entries:
  "qwer2" => 2
  "asdf"  => 3
  "qwer1" => 1

julia> foo["q[TAB]

"qwer1" "qwer2"
julia> foo["qwer
```

La finalización con tabulador también puede ayudar a completar campos:

```julia-repl
julia> x = 3 + 4im;

julia> x.[TAB][TAB]
im re

julia> import UUIDs

julia> UUIDs.uuid[TAB][TAB]
uuid1        uuid4         uuid5        uuid_version
```

Los campos para la salida de funciones también se pueden completar:

```julia-repl
julia> split("","")[1].[TAB]
lastindex  offset  string
```

La finalización de campos para la salida de funciones utiliza la inferencia de tipos, y solo puede sugerir campos si la función es estable en tipos.

La finalización de tabulaciones puede ayudar con la investigación de los métodos disponibles que coinciden con los argumentos de entrada:

```julia-repl
julia> max([TAB] # All methods are displayed, not shown here due to size of the list

julia> max([1, 2], [TAB] # All methods where `Vector{Int}` matches as first argument
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281

julia> max([1, 2], max(1, 2), [TAB] # All methods matching the arguments.
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281
```

Las palabras clave también se muestran en los métodos sugeridos después de `;`, vea la línea a continuación donde `limit` y `keepempty` son argumentos de palabras clave:

```julia-repl
julia> split("1 1 1", [TAB]
split(str::AbstractString; limit, keepempty) in Base at strings/util.jl:302
split(str::T, splitter; limit, keepempty) where T<:AbstractString in Base at strings/util.jl:277
```

La finalización de los métodos utiliza inferencia de tipos y, por lo tanto, puede ver si los argumentos coinciden incluso si los argumentos son el resultado de funciones. La función debe ser estable en tipos para que la finalización pueda eliminar métodos que no coinciden.

Si te preguntas qué métodos se pueden usar con tipos de argumentos particulares, usa `?` como el nombre de la función. Esto muestra un ejemplo de búsqueda de funciones en InteractiveUtils que aceptan una sola cadena:

```julia-repl
julia> InteractiveUtils.?("somefile")[TAB]
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
```

Estos métodos enumerados en el módulo `InteractiveUtils` que se pueden llamar en una cadena. Por defecto, esto excluye los métodos donde todos los argumentos están tipados como `Any`, pero también puedes ver esos manteniendo presionado SHIFT-TAB en lugar de TAB:

```julia-repl
julia> InteractiveUtils.?("somefile")[SHIFT-TAB]
apropos(string) in REPL at REPL/src/docview.jl:796
clipboard(x) in InteractiveUtils at InteractiveUtils/src/clipboard.jl:64
code_llvm(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:221
code_native(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:243
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
edit(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:225
eval(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
include(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
less(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:274
report_bug(kind) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:391
separate_kwargs(args...; kwargs...) in InteractiveUtils at InteractiveUtils/src/macros.jl:7
```

También puedes usar `?("somefile")[TAB]` y buscar en todos los módulos, pero las listas de métodos pueden ser largas.

Al omitir el paréntesis de cierre, puedes incluir funciones que podrían requerir argumentos adicionales:

```julia-repl
julia> using Mmap

help?> Mmap.?("file",[TAB]
Mmap.Anonymous(name::String, readonly::Bool, create::Bool) in Mmap at Mmap/src/Mmap.jl:16
mmap(file::AbstractString) in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}) where T<:Array in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
```

## Customizing Colors

Los colores utilizados por Julia y el REPL también se pueden personalizar. Para cambiar el color del aviso de Julia, puedes agregar algo como lo siguiente a tu archivo `~/.julia/config/startup.jl`, que debe colocarse dentro de tu directorio personal:

```julia
function customize_colors(repl)
    repl.prompt_color = Base.text_colors[:cyan]
end

atreplinit(customize_colors)
```

Las claves de color disponibles se pueden ver escribiendo `Base.text_colors` en el modo de ayuda del REPL. Además, los enteros del 0 al 255 se pueden usar como claves de color para terminales con soporte de 256 colores.

También puedes cambiar los colores para los mensajes de ayuda y los prompts de shell, así como el texto de entrada y respuesta, configurando el campo apropiado de `repl` en la función `customize_colors` anterior (respectivamente, `help_color`, `shell_color`, `input_color` y `answer_color`). Para los dos últimos, asegúrate de que el campo `envcolors` también esté configurado en falso.

También es posible aplicar formato en negrita utilizando `Base.text_colors[:bold]` como un color. Por ejemplo, para imprimir respuestas en fuente negrita, se puede usar lo siguiente como un `~/.julia/config/startup.jl`:

```julia
function customize_colors(repl)
    repl.envcolors = false
    repl.answer_color = Base.text_colors[:bold]
end

atreplinit(customize_colors)
```

También puedes personalizar el color utilizado para renderizar mensajes de advertencia e informativos configurando las variables de entorno apropiadas. Por ejemplo, para renderizar mensajes de error, advertencia e informativos respectivamente en magenta, amarillo y cian, puedes agregar lo siguiente a tu archivo `~/.julia/config/startup.jl`:

```julia
ENV["JULIA_ERROR_COLOR"] = :magenta
ENV["JULIA_WARN_COLOR"] = :yellow
ENV["JULIA_INFO_COLOR"] = :cyan
```

## Changing the contextual module which is active at the REPL

Al ingresar expresiones en el REPL, por defecto se evalúan en el módulo `Main`;

```julia-repl
julia> @__MODULE__
Main
```

Es posible cambiar este módulo contextual a través de la función `REPL.activate(m)` donde `m` es un `Módulo` o escribiendo el módulo en el REPL y presionando la combinación de teclas Alt-m con el cursor sobre el nombre del módulo (Esc-m en MacOS). Presionar la combinación de teclas en un aviso vacío alterna el contexto entre el módulo no-`Main` previamente activo y `Main`. El módulo activo se muestra en el aviso (a menos que sea `Main`):

```julia-repl
julia> using REPL

julia> REPL.activate(Base)

(Base) julia> @__MODULE__
Base

(Base) julia> using REPL # Need to load REPL into Base module to use it

(Base) julia> REPL.activate(Main)

julia>

julia> Core<Alt-m> # using the keybinding to change module

(Core) julia>

(Core) julia> <Alt-m> # going back to Main via keybinding

julia>

julia> <Alt-m> # going back to previously-active Core via keybinding

(Core) julia>
```

Las funciones que toman un argumento de módulo opcional a menudo predeterminan al módulo del contexto REPL. Como ejemplo, llamar a `varinfo()` mostrará las variables del módulo activo actual:

```julia-repl
julia> module CustomMod
           export var, f
           var = 1
           f(x) = x^2
       end;

julia> REPL.activate(CustomMod)

(Main.CustomMod) julia> varinfo()
  name         size summary
  ––––––––– ––––––– ––––––––––––––––––––––––––––––––––
  CustomMod         Module
  f         0 bytes f (generic function with 1 method)
  var       8 bytes Int64
```

## Numbered prompt

Es posible obtener una interfaz que sea similar al REPL de IPython y al cuaderno de Mathematica con indicaciones de entrada numeradas y prefijos de salida. Esto se hace llamando a `REPL.numbered_prompt!()`. Si deseas tener esto habilitado al inicio, agrega

```julia
atreplinit() do repl
    @eval import REPL
    if !isdefined(repl, :interface)
        repl.interface = REPL.setup_interface(repl)
    end
    REPL.numbered_prompt!(repl)
end
```

en tu archivo `startup.jl`. En el aviso numerado, la variable `Out[n]` (donde `n` es un entero) se puede usar para referirse a resultados anteriores:

```julia-repl
In [1]: 5 + 3
Out[1]: 8

In [2]: Out[1] + 5
Out[2]: 13

In [3]: Out
Out[3]: Dict{Int64, Any} with 2 entries:
  2 => 13
  1 => 8
```

!!! note
    Dado que todas las salidas de las evaluaciones REPL anteriores se guardan en la variable `Out`, se debe tener cuidado si se están devolviendo muchos objetos grandes en memoria, como arreglos, ya que estarán protegidos de la recolección de basura mientras exista una referencia a ellos en `Out`. Si necesitas eliminar referencias a objetos en `Out`, puedes borrar todo el historial que almacena con `empty!(Out)`, o borrar una entrada individual con `Out[n] = nothing`.


## TerminalMenus

TerminalMenus es un submódulo del REPL de Julia y permite menús interactivos pequeños y de bajo perfil en la terminal.

### Examples

```julia
import REPL
using REPL.TerminalMenus

options = ["apple", "orange", "grape", "strawberry",
            "blueberry", "peach", "lemon", "lime"]

```

#### RadioMenu

El RadioMenu permite al usuario seleccionar una opción de la lista. La función `request` muestra el menú interactivo y devuelve el índice de la opción seleccionada. Si un usuario presiona 'q' o `ctrl-c`, `request` devolverá un `-1`.

```julia
# `pagesize` is the number of items to be displayed at a time.
#  The UI will scroll if the number of options is greater
#   than the `pagesize`
menu = RadioMenu(options, pagesize=4)

# `request` displays the menu and returns the index after the
#   user has selected a choice
choice = request("Choose your favorite fruit:", menu)

if choice != -1
    println("Your favorite fruit is ", options[choice], "!")
else
    println("Menu canceled.")
end

```

Por favor, proporciona el contenido en Markdown que deseas traducir al español.

```
Choose your favorite fruit:
^  grape
   strawberry
 > blueberry
v  peach
Your favorite fruit is blueberry!
```

#### MultiSelectMenu

El MultiSelectMenu permite a los usuarios seleccionar múltiples opciones de una lista.

```julia
# here we use the default `pagesize` 10
menu = MultiSelectMenu(options)

# `request` returns a `Set` of selected indices
# if the menu us canceled (ctrl-c or q), return an empty set
choices = request("Select the fruits you like:", menu)

if length(choices) > 0
    println("You like the following fruits:")
    for i in choices
        println("  - ", options[i])
    end
else
    println("Menu canceled.")
end
```

Por favor, proporciona el contenido en Markdown que deseas traducir al español.

```
Select the fruits you like:
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
 > [X] orange
   [X] grape
   [ ] strawberry
   [ ] blueberry
   [X] peach
   [ ] lemon
   [ ] lime
You like the following fruits:
  - orange
  - grape
  - peach
```

### Customization / Configuration

#### ConfiguredMenu subtypes

A partir de Julia 1.6, la forma recomendada de configurar menús es a través del constructor. Por ejemplo, el menú de selección múltiple predeterminado

```
julia> menu = MultiSelectMenu(options, pagesize=5);

julia> request(menu) # ASCII is used by default
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
   [X] orange
   [ ] grape
 > [X] strawberry
v  [ ] blueberry
```

puede en su lugar ser representado con caracteres de selección y navegación Unicode con

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode);

julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   ⬚ apple
   ✓ orange
   ⬚ grape
 → ✓ strawberry
↓  ⬚ blueberry
```

También es posible una configuración más detallada:

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode, checked="YEP!", unchecked="NOPE", cursor='⧐');

julia> request(menu)
julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   NOPE apple
   YEP! orange
   NOPE grape
 ⧐ YEP! strawberry
↓  NOPE blueberry
```

Aparte de la opción general `charset`, para `RadioMenu` las opciones configurables son:

  * `cursor::Char='>'|'→'`: carácter a utilizar para el cursor
  * `up_arrow::Char='^'|'↑'`: carácter a utilizar para la flecha hacia arriba
  * `down_arrow::Char='v'|'↓'`: carácter a utilizar para la flecha hacia abajo
  * `updown_arrow::Char='I'|'↕'`: carácter a utilizar para la flecha arriba/abajo en una página de una línea
  * `scroll_wrap::Bool=false`: opcionalmente envolver al principio/final de un menú
  * `ctrl_c_interrupt::Bool=true`: Si `false`, devuelve vacío en ^C, si `true` lanza InterruptException() en ^C

`MultiSelectMenu` agrega:

  * `checked::String="[X]"|"✓"`: cadena a usar para marcado
  * `unchecked::String="[ ]"|"⬚")`: cadena a usar para no marcado

Puedes crear nuevos tipos de menús propios. Los tipos que se derivan de `TerminalMenus.ConfiguredMenu` configuran las opciones del menú en el momento de la construcción.

#### Legacy interface

Antes de Julia 1.6, y aún soportado en Julia 1.x, también se puede configurar menús llamando a `TerminalMenus.config()`.

## References

### REPL

```@docs
Base.atreplinit
```

### TerminalMenus

### Menus

```@docs
REPL.TerminalMenus.RadioMenu
REPL.TerminalMenus.MultiSelectMenu
```

#### Configuration

```@docs
REPL.TerminalMenus.Config
REPL.TerminalMenus.MultiSelectConfig
REPL.TerminalMenus.config
```

#### User interaction

```@docs
REPL.TerminalMenus.request
```

#### AbstractMenu extension interface

Cualquier subtipo de `AbstractMenu` debe ser mutable y debe contener los campos `pagesize::Int` y `pageoffset::Int`. Cualquier subtipo también debe implementar las siguientes funciones:

```@docs
REPL.TerminalMenus.pick
REPL.TerminalMenus.cancel
REPL.TerminalMenus.writeline
```

También debe implementar `options` o `numoptions`:

```@docs
REPL.TerminalMenus.options
REPL.TerminalMenus.numoptions
```

Si el subtipo no tiene un campo llamado `selected`, también debe implementar

```@docs
REPL.TerminalMenus.selected
```

Lo siguiente es opcional, pero puede permitir una personalización adicional:

```@docs
REPL.TerminalMenus.header
REPL.TerminalMenus.keypress
```
