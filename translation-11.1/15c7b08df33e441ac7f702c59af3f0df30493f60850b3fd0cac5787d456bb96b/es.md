# [StyledStrings](@id stdlib-styledstrings)

```@meta
CurrentModule = StyledStrings
DocTestSetup = quote
    using StyledStrings
end
```

!!! note
    La API para StyledStrings y AnnotatedStrings se considera experimental y está sujeta a cambios entre versiones de Julia.


## [Styling](@id stdlib-styledstrings-styling)

Cuando se trabaja con cadenas, el formato y el estilo a menudo aparecen como una preocupación secundaria.

Por ejemplo, al imprimir en un terminal, es posible que desees esparcir [ANSI escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code#SGR_(Select_Graphic_Rendition)_parameters) en la salida. Al generar construcciones de estilo HTML (`<span style="...">`, etc.), se cumple un propósito similar, y así sucesivamente. Es posible simplemente insertar las construcciones de estilo en bruto en la cadena junto al contenido mismo, pero rápidamente se hace evidente que esto no es adecuado para nada más que los casos de uso más básicos. No todos los terminales admiten los mismos códigos ANSI, las construcciones de estilo deben ser meticulosamente eliminadas al calcular el ancho del contenido ya estilizado, y eso es antes de que incluso comiences a manejar múltiples formatos de salida.

En lugar de dejar que este dolor de cabeza sea ampliamente experimentado en la parte inferior, se aborda de manera directa mediante la introducción de un tipo de cadena especial ([`AnnotatedString`](@ref Base.AnnotatedString)). Este tipo de cadena envuelve cualquier otro tipo [`AbstractString`](@ref) y permite que se apliquen información de formato a regiones (por ejemplo, los caracteres del 1 al 7 son negrita y rojos).

Las regiones de una cadena se estilizan aplicando [`Face`](@ref StyledStrings.Face) (piensa en "tipografía") a ellas: una estructura que contiene información de estilo. Como conveniencia, las tipografías en el diccionario global de tipografías (por ejemplo, `shadow`) pueden ser nombradas en lugar de dar el `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` directamente.

Junto con estas capacidades, también proporcionamos una forma conveniente de construir [`AnnotatedString`](@ref Base.AnnotatedString), detallado en [Styled String Literals](@ref stdlib-styledstring-literals).

```@repl demo
using StyledStrings
styled"{yellow:hello} {blue:there}"
```

## [Annotated Strings](@id man-annotated-strings)

A veces es útil poder mantener metadatos relacionados con regiones de una cadena. Un [`AnnotatedString`](@ref Base.AnnotatedString) envuelve otra cadena y permite que las regiones de esta sean anotadas con valores etiquetados (`:label => value`). Todas las operaciones de cadena genéricas se aplican a la cadena subyacente. Sin embargo, cuando es posible, se preserva la información de estilo. Esto significa que puedes manipular un `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` —tomando subcadenas, rellenándolas, concatenándolas con otras cadenas— y las anotaciones de metadatos "vendrán junto con el viaje".

Este tipo de cadena es fundamental para el [StyledStrings stdlib](@ref stdlib-styledstrings), que utiliza anotaciones etiquetadas con `:face` para mantener información de estilo.

Al concatenar un [`AnnotatedString`](@ref Base.AnnotatedString), asegúrate de usar [`annotatedstring`](@ref StyledStrings.annotatedstring) en lugar de [`string`](@ref) si deseas mantener las anotaciones de cadena.

```jldoctest
julia> str = AnnotatedString("hello there", [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
AnnotatedString{String}

julia> str2 = AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == annotatedstring(str, str2) # *-concatenation works
true
```

Las anotaciones de un [`AnnotatedString`](@ref Base.AnnotatedString) se pueden acceder y modificar a través de las funciones [`annotations`](@ref StyledStrings.annotations) y [`annotate!`](@ref StyledStrings.annotate!).

## Styling via [`AnnotatedString`](@ref Base.AnnotatedString)s

## [Faces](@id stdlib-styledstrings-faces)

### The `Face` type

Un [`Face`](@ref StyledStrings.Face) especifica detalles de una tipografía en la que se puede establecer texto. Cubre un conjunto de atributos básicos que se generalizan bien en diferentes formatos, a saber:

  * `fuente`
  * `altura`
  * `peso`
  * `inclinación`
  * `primer plano`
  * `fondo`
  * `subrayar`
  * `tachado`
  * `inverso`
  * `heredar`

Para obtener detalles sobre las formas particulares que toman estos atributos, consulta el [`Face`](@ref StyledStrings.Face) docstring, pero de particular interés es `inherit`, ya que te permite *heredar* atributos de otros `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`s.

### The global faces dictionary

Para hacer que la referencia a estilos particulares sea más conveniente, hay un `Dict{Symbol, Face}` global que permite que los [`Face`](@ref StyledStrings.Face) se refieran simplemente por nombre. Los paquetes pueden agregar caras a este diccionario a través de la función [`addface!`](@ref StyledStrings.addface!), y las caras cargadas pueden ser fácilmente [customized](@ref stdlib-styledstrings-face-toml).

!!! warning "Appropriate face naming"
    Cualquier paquete que registre nuevas caras debe asegurarse de que estén precedidas por el nombre del paquete, es decir, seguir el formato `mypackage_myface`. Esto es importante para la previsibilidad y para prevenir conflictos de nombres.

    Además, los paquetes deben tener cuidado de usar (e introducir) caras *semánticas* (como `code`) en lugar de colores y estilos directos (como `cyan`). Esto es útil de varias maneras, desde hacer que la intención en el uso sea más obvia, ayudar a la composabilidad y hacer que la personalización del usuario sea más intuitiva.


Hay dos conjuntos de exenciones a la regla del prefijo del paquete:

  * el conjunto de caras básicas que son parte del valor predeterminado del diccionario de caras
  * caras introducidas por la propia biblioteca estándar de Julia, a saber, `JuliaSyntaxHighlighting`

#### [Basic faces](@id stdlib-styledstrings-basic-faces)

Las caras básicas están destinadas a representar una idea general que es ampliamente aplicable.

Para establecer un texto con un cierto atributo, tenemos las caras `negrita`, `ligera`, `cursiva`, `subrayado`, `tachado` e `inversa`.

También hay nombres para los 16 colores terminales: `negro`, `rojo`, `verde`, `amarillo`, `azul`, `magenta`, `cian`, `blanco`, `negro_brillante`/`gris`, `rojo_brillante`, `verde_brillante`, `azul_brillante`, `magenta_brillante`, `cian_brillante` y `blanco_brillante`.

Para el texto sombreado (es decir, tenue pero presente) existe la cara `shadow`. Para indicar una región seleccionada, está la cara `region`. De manera similar, para énfasis y resaltado se definen las caras `emphasis` y `highlight`. También hay `code` para texto similar al código.

Para indicar visualmente la gravedad de los mensajes, se definen las caras de `error`, `warning`, `success`, `info`, `note` y `tip`.

### [Customisation of faces (`Faces.toml`)](@id stdlib-styledstrings-face-toml)

Es bueno que los nombres de las caras en el diccionario global de caras sean personalizables. La tematización y la estética son agradables, y también es importante por razones de accesibilidad. Un archivo TOML se puede analizar en una lista de [`Face`](@ref StyledStrings.Face) especificaciones que se fusionan con la entrada preexistente en el diccionario de caras.

Un [`Face`](@ref StyledStrings.Face) se representa en TOML de la siguiente manera:

```toml
[facename]
attribute = "value"
...

[package.facename]
attribute = "value"
```

Por ejemplo, si la cara `shadow` es demasiado difícil de leer, se puede hacer más brillante así:

```toml
[shadow]
foreground = "white"
```

Al iniciar, se carga el archivo `config/faces.toml` en el primer depósito de Julia (generalmente `~/.julia`).

### Applying faces to a `AnnotatedString`

Por convención, los atributos `:face` de un [`AnnotatedString`](@ref Base.AnnotatedString) contienen información sobre los [`Face`](@ref StyledStrings.Face) que actualmente se aplican. Esto se puede dar en múltiples formas, como un único `Symbol` que nombra un `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` en el diccionario de caras global, un `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` en sí, o un vector de cualquiera de ellos.

Los métodos `show(::IO, ::MIME"text/plain", ::AnnotatedString)` y `show(::IO, ::MIME"text/html", ::AnnotatedString)` ambos examinan los atributos `:face` y los combinan todos al determinar el estilo general.

Podemos suministrar atributos `:face` a un `AnnotatedString` durante la construcción, agregarlos a la lista de propiedades después, o usar el conveniente [Styled String literals](@ref stdlib-styledstring-literals).

```@repl demo
str1 = AnnotatedString("blue text", [(1:9, :face, :blue)])
str2 = styled"{blue:blue text}"
str1 == str2
sprint(print, str1, context = :color => true)
sprint(show, MIME("text/html"), str1, context = :color => true)
```

## [Styled String Literals](@id stdlib-styledstring-literals)

Para facilitar la construcción de [`AnnotatedString`](@ref Base.AnnotatedString)s con [`Face`](@ref StyledStrings.Face)s aplicados, el literal de cadena estilizado [`styled"..."`](@ref @styled_str) permite que el contenido y los atributos se expresen fácilmente juntos a través de una gramática personalizada.

Dentro de un literal [`styled"..."`](@ref @styled_str), las llaves se consideran caracteres especiales y deben ser escapadas en el uso normal (`\{`, `\}`). Esto permite que se utilicen para expresar anotaciones con construcciones `{anotaciones...:texto}` (anidables).

El componente `annotations...` es una lista separada por comas de tres tipos de anotaciones.

  * Nombres de cara
  * Expresiones `Face` en línea `(clave=valor,...)`
  * `clave=valor` pares

La interpolación es posible en todas partes excepto para las claves de cara en línea.

Para más información sobre la gramática, consulte la ayuda extendida del docstring [`styled"..."`](@ref @styled_str).

Como ejemplo, podemos demostrar la lista de caras integradas mencionadas anteriormente de la siguiente manera:

```julia-repl
julia> println(styled"
The basic font-style attributes are {bold:bold}, {light:light}, {italic:italic},
{underline:underline}, and {strikethrough:strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:
 {black:■} {red:■} {green:■} {yellow:■} {blue:■} {magenta:■} {cyan:■} {white:■}
 {bright_black:■} {bright_red:■} {bright_green:■} {bright_yellow:■} {bright_blue:■} {bright_magenta:■} {bright_cyan:■} {bright_white:■}

Since {code:bright_black} is effectively grey, we define two aliases for it:
{code:grey} and {code:gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the
{code:inverse} face, for example: {magenta:some {inverse:inverse} text}.

The intent-based basic faces are {shadow:shadow} (for dim but visible text),
{region:region} for selections, {emphasis:emphasis}, and {highlight:highlight}.
As above, {code:code} is used for code-like text.

Lastly, we have the 'message severity' faces: {error:error}, {warning:warning},
{success:success}, {info:info}, {note:note}, and {tip:tip}.

Remember that all these faces (and any user or package-defined ones) can
arbitrarily nest and overlap, {region,tip:like {bold,italic:so}}.")
```

```@raw comment
Documenter doesn't properly represent all the styling above, so I've converted it manually to HTML and LaTeX.
```

```@raw html
<pre>
 The basic font-style attributes are <span style="font-weight: 700;">bold</span>, <span style="font-weight: 300;">light</span>, <span style="font-style: italic;">italic</span>,
 <span style="text-decoration: underline;">underline</span>, and <span style="text-decoration: line-through">strikethrough</span>.

 In terms of color, we have named faces for the 16 standard terminal colors:
  <span style="color: #1c1a23;">■</span> <span style="color: #a51c2c;">■</span> <span style="color: #25a268;">■</span> <span style="color: #e5a509;">■</span> <span style="color: #195eb3;">■</span> <span style="color: #803d9b;">■</span> <span style="color: #0097a7;">■</span> <span style="color: #dddcd9;">■</span>
  <span style="color: #76757a;">■</span> <span style="color: #ed333b;">■</span> <span style="color: #33d079;">■</span> <span style="color: #f6d22c;">■</span> <span style="color: #3583e4;">■</span> <span style="color: #bf60ca;">■</span> <span style="color: #26c6da;">■</span> <span style="color: #f6f5f4;">■</span>

 Since <span style="color: #0097a7;">bright_black</span> is effectively grey, we define two aliases for it:
 <span style="color: #0097a7;">grey</span> and <span style="color: #0097a7;">gray</span> to allow for regional spelling differences.

 To flip the foreground and background colors of some text, you can use the
 <span style="color: #0097a7;">inverse</span> face, for example: <span style="color: #803d9b;">some </span><span style="background-color: #803d9b;">inverse</span><span style="color: #803d9b;"> text</span>.

 The intent-based basic faces are <span style="color: #76757a;">shadow</span> (for dim but visible text),
 <span style="background-color: #3a3a3a;">region</span> for selections, <span style="color: #195eb3;">emphasis</span>, and <span style="background-color: #195eb3;">highlight</span>.
 As above, <span style="color: #0097a7;">code</span> is used for code-like text.

 Lastly, we have the 'message severity' faces: <span style="color: #ed333b;">error</span>, <span style="color: #e5a509;">warning</span>,
 <span style="color: #25a268;">success</span>, <span style="color: #26c6da;">info</span>, <span style="color: #76757a;">note</span>, and <span style="color: #33d079;">tip</span>.

 Remember that all these faces (and any user or package-defined ones) can
 arbitrarily nest and overlap, <span style="color: #33d079;background-color: #3a3a3a;">like <span style="font-weight: 700;font-style: italic;">so</span></span>.</pre>
```

```@raw latex
\begingroup
\ttfamily
\setlength{\parindent}{0pt}
\setlength{\parskip}{\baselineskip}

The basic font-style attributes are {\fontseries{b}\selectfont bold}, {\fontseries{l}\selectfont light}, {\fontshape{it}\selectfont italic},\\
\underline{underline}, and {strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:\\
{\color[HTML]{1c1a23}\(\blacksquare\)} {\color[HTML]{a51c2c}\(\blacksquare\)} {\color[HTML]{25a268}\(\blacksquare\)}
{\color[HTML]{e5a509}\(\blacksquare\)} {\color[HTML]{195eb3}\(\blacksquare\)} {\color[HTML]{803d9b}\(\blacksquare\)}
{\color[HTML]{0097a7}\(\blacksquare\)} {\color[HTML]{dddcd9}\(\blacksquare\)} \\
{\color[HTML]{76757a}\(\blacksquare\)} {\color[HTML]{ed333b}\(\blacksquare\)} {\color[HTML]{33d079}\(\blacksquare\)} {\color[HTML]{f6d22c}\(\blacksquare\)} {\color[HTML]{3583e4}\(\blacksquare\)} {\color[HTML]{bf60ca}\(\blacksquare\)} {\color[HTML]{26c6da}\(\blacksquare\)} {\color[HTML]{f6f5f4}\(\blacksquare\)}

Since {\color[HTML]{0097a7}bright\_black} is effectively grey, we define two aliases for it:\\
{\color[HTML]{0097a7}grey} and {\color[HTML]{0097a7}gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the\\
{\color[HTML]{0097a7}inverse} face, for example: {\color[HTML]{803d9b}some \colorbox[HTML]{803d9b}{\color[HTML]{000000}inverse} text}.

The intent-based basic faces are {\color[HTML]{76757a}shadow} (for dim but visible text),\\
\colorbox[HTML]{3a3a3a}{region} for selections, {\color[HTML]{195eb3}emphasis}, and \colorbox[HTML]{195eb3}{highlight}.\\
As above, {\color[HTML]{0097a7}code} is used for code-like text.

Lastly, we have the 'message severity' faces: {\color[HTML]{ed333b}error}, {\color[HTML]{e5a509}warning},\\
{\color[HTML]{25a268}success}, {\color[HTML]{26c6da}info}, {\color[HTML]{76757a}note}, and {\color[HTML]{33d079}tip}.

Remember that all these faces (and any user or package-defined ones) can\\
arbitrarily nest and overlap, \colorbox[HTML]{3a3a3a}{\color[HTML]{33d079}like
  {\fontseries{b}\fontshape{it}\selectfont so}}.
\endgroup
```

## [API reference](@id stdlib-styledstrings-api)

### Styling and Faces

```@docs
StyledStrings.@styled_str
StyledStrings.styled
StyledStrings.Face
StyledStrings.addface!
StyledStrings.withfaces
StyledStrings.SimpleColor
StyledStrings.parse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.tryparse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.merge(::StyledStrings.Face, ::StyledStrings.Face)
```
