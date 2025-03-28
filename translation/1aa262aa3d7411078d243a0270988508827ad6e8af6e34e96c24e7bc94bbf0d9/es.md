# [Strings](@id man-strings)

Las cadenas son secuencias finitas de caracteres. Por supuesto, el verdadero problema surge cuando uno pregunta qué es un carácter. Los caracteres con los que los hablantes de inglés están familiarizados son las letras `A`, `B`, `C`, etc., junto con los números y los símbolos de puntuación comunes. Estos caracteres están estandarizados junto con un mapeo a valores enteros entre 0 y 127 por el estándar [ASCII](https://en.wikipedia.org/wiki/ASCII). Hay, por supuesto, muchos otros caracteres utilizados en idiomas no ingleses, incluidos variantes de los caracteres ASCII con acentos y otras modificaciones, escrituras relacionadas como el cirílico y el griego, y escrituras completamente no relacionadas con ASCII e inglés, incluyendo árabe, chino, hebreo, hindi, japonés y coreano. El estándar [Unicode](https://en.wikipedia.org/wiki/Unicode) aborda las complejidades de lo que exactamente es un carácter, y se acepta generalmente como el estándar definitivo que aborda este problema. Dependiendo de tus necesidades, puedes ignorar estas complejidades por completo y simplemente pretender que solo existen caracteres ASCII, o puedes escribir código que pueda manejar cualquiera de los caracteres o codificaciones que uno puede encontrar al manejar texto no ASCII. Julia hace que tratar con texto ASCII simple sea simple y eficiente, y manejar Unicode es tan simple y eficiente como sea posible. En particular, puedes escribir código de cadena estilo C para procesar cadenas ASCII, y funcionarán como se espera, tanto en términos de rendimiento como de semántica. Si dicho código encuentra texto no ASCII, fallará de manera elegante con un mensaje de error claro, en lugar de introducir silenciosamente resultados corruptos. Cuando esto sucede, modificar el código para manejar datos no ASCII es sencillo.

Hay algunas características destacadas a nivel alto sobre las cadenas de Julia:

  * El tipo de concreto incorporado utilizado para cadenas (y literales de cadena) en Julia es [`String`](@ref). Esto admite el rango completo de [Unicode](https://en.wikipedia.org/wiki/Unicode) caracteres a través de la codificación [UTF-8](https://en.wikipedia.org/wiki/UTF-8). (Se proporciona una función [`transcode`](@ref) para convertir entre otras codificaciones Unicode.)
  * Todos los tipos de cadena son subtipos del tipo abstracto `AbstractString`, y los paquetes externos definen subtipos adicionales de `AbstractString` (por ejemplo, para otras codificaciones). Si defines una función que espera un argumento de cadena, debes declarar el tipo como `AbstractString` para aceptar cualquier tipo de cadena.
  * Al igual que C y Java, pero a diferencia de la mayoría de los lenguajes dinámicos, Julia tiene un tipo de primera clase para representar un solo carácter, llamado [`AbstractChar`](@ref). El subtipo incorporado [`Char`](@ref) de `AbstractChar` es un tipo primitivo de 32 bits que puede representar cualquier carácter Unicode (y que se basa en la codificación UTF-8).
  * Como en Java, las cadenas son inmutables: el valor de un objeto `AbstractString` no puede ser cambiado. Para construir un valor de cadena diferente, se construye una nueva cadena a partir de partes de otras cadenas.
  * Conceptualmente, una cadena es una *función parcial* de índices a caracteres: para algunos valores de índice, no se devuelve ningún valor de carácter y, en su lugar, se lanza una excepción. Esto permite un indexado eficiente en cadenas por el índice de byte de una representación codificada en lugar de por un índice de carácter, lo que no se puede implementar de manera eficiente y simple para codificaciones de ancho variable de cadenas Unicode.

## [Characters](@id man-characters)

Un valor `Char` representa un solo carácter: es simplemente un tipo primitivo de 32 bits con una representación literal especial y comportamientos aritméticos apropiados, y que puede ser convertido a un valor numérico que representa un [Unicode code point](https://en.wikipedia.org/wiki/Code_point).  (Los paquetes de Julia pueden definir otros subtipos de `AbstractChar`, por ejemplo, para optimizar operaciones para otros [text encodings](https://en.wikipedia.org/wiki/Character_encoding).) Aquí se muestra cómo se ingresan y se muestran los valores `Char` (ten en cuenta que los literales de carácter están delimitados con comillas simples, no con comillas dobles):

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> typeof(c)
Char
```

Puedes convertir fácilmente un `Char` a su valor entero, es decir, el punto de código:

```jldoctest
julia> c = Int('x')
120

julia> typeof(c)
Int64
```

En arquitecturas de 32 bits, [`typeof(c)`](@ref) será [`Int32`](@ref). Puedes convertir un valor entero de vuelta a un `Char` con la misma facilidad:

```jldoctest
julia> Char(120)
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)
```

No todos los valores enteros son puntos de código Unicode válidos, pero por rendimiento, la conversión `Char` no verifica que cada valor de carácter sea válido. Si deseas comprobar que cada valor convertido es un punto de código válido, utiliza la función [`isvalid`](@ref):

```jldoctest
julia> Char(0x110000)
'\U110000': Unicode U+110000 (category In: Invalid, too high)

julia> isvalid(Char, 0x110000)
false
```

A partir de este escrito, los puntos de código Unicode válidos son `U+0000` hasta `U+D7FF` y `U+E000` hasta `U+10FFFF`. No todos han sido asignados a significados inteligibles aún, ni necesariamente son interpretables por aplicaciones, pero todos estos valores se consideran caracteres Unicode válidos.

Puedes ingresar cualquier carácter Unicode entre comillas simples usando `\u` seguido de hasta cuatro dígitos hexadecimales o `\U` seguido de hasta ocho dígitos hexadecimales (el valor válido más largo solo requiere seis):

```jldoctest
julia> '\u0'
'\0': ASCII/Unicode U+0000 (category Cc: Other, control)

julia> '\u78'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> '\u2200'
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> '\U10ffff'
'\U10ffff': Unicode U+10FFFF (category Cn: Other, not assigned)
```

Julia utiliza la configuración regional y de idioma de tu sistema para determinar qué caracteres se pueden imprimir tal cual y cuáles deben ser mostrados utilizando las formas de entrada genéricas y escapadas `\u` o `\U`. Además de estas formas de escape Unicode, todo [C's traditional escaped input forms](https://en.wikipedia.org/wiki/C_syntax#Backslash_escapes) también se puede utilizar:

```jldoctest
julia> Int('\0')
0

julia> Int('\t')
9

julia> Int('\n')
10

julia> Int('\e')
27

julia> Int('\x7f')
127

julia> Int('\177')
127
```

Puedes hacer comparaciones y una cantidad limitada de aritmética con valores `Char`:

```jldoctest
julia> 'A' < 'a'
true

julia> 'A' <= 'a' <= 'Z'
false

julia> 'A' <= 'X' <= 'Z'
true

julia> 'x' - 'a'
23

julia> 'A' + 1
'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
```

## String Basics

Las literales de cadena están delimitadas por comillas dobles o comillas dobles triples (no comillas simples):

```jldoctest helloworldstring
julia> str = "Hello, world.\n"
"Hello, world.\n"

julia> """Contains "quote" characters"""
"Contains \"quote\" characters"
```

Las líneas largas en cadenas se pueden dividir precediendo la nueva línea con una barra invertida (`\`):

```jldoctest
julia> "This is a long \
       line"
"This is a long line"
```

Si deseas extraer un carácter de una cadena, debes indexarla:

```jldoctest helloworldstring
julia> str[begin]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[1]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[end]
'\n': ASCII/Unicode U+000A (category Cc: Other, control)
```

Muchos objetos de Julia, incluidos los strings, se pueden indexar con enteros. El índice del primer elemento (el primer carácter de un string) se devuelve con [`firstindex(str)`](@ref), y el índice del último elemento (carácter) con [`lastindex(str)`](@ref). Las palabras clave `begin` y `end` se pueden usar dentro de una operación de indexación como abreviaturas para los primeros y últimos índices, respectivamente, a lo largo de la dimensión dada. La indexación de strings, como la mayoría de las indexaciones en Julia, es basada en 1: `firstindex` siempre devuelve `1` para cualquier `AbstractString`. Sin embargo, como veremos a continuación, `lastindex(str)` *no* es en general lo mismo que `length(str)` para un string, porque algunos caracteres Unicode pueden ocupar múltiples "unidades de código".

Puedes realizar operaciones aritméticas y otras operaciones con [`end`](@ref), al igual que un valor normal:

```jldoctest helloworldstring
julia> str[end-1]
'.': ASCII/Unicode U+002E (category Po: Punctuation, other)

julia> str[end÷2]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

Usar un índice menor que `begin` (`1`) o mayor que `end` genera un error:

```jldoctest helloworldstring
julia> str[begin-1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [0]
[...]

julia> str[end+1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [15]
[...]
```

También puedes extraer una subcadena utilizando la indexación por rango:

```jldoctest helloworldstring
julia> str[4:9]
"lo, wo"
```

Tenga en cuenta que las expresiones `str[k]` y `str[k:k]` no dan el mismo resultado:

```jldoctest helloworldstring
julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[6:6]
","
```

El primero es un valor de un solo carácter de tipo `Char`, mientras que el segundo es un valor de cadena que contiene solo un solo carácter. En Julia, estas son cosas muy diferentes.

El indexado por rango crea una copia de la parte seleccionada de la cadena original. Alternativamente, es posible crear una vista en una cadena utilizando el tipo [`SubString`](@ref). Más simplemente, usar la macro [`@views`](@ref) en un bloque de código convierte todos los fragmentos de cadena en subcadenas. Por ejemplo:

```jldoctest
julia> str = "long string"
"long string"

julia> substr = SubString(str, 1, 4)
"long"

julia> typeof(substr)
SubString{String}

julia> @views typeof(str[1:4]) # @views converts slices to SubStrings
SubString{String}
```

Varias funciones estándar como [`chop`](@ref), [`chomp`](@ref) o [`strip`](@ref) devuelven un [`SubString`](@ref).

## Unicode and UTF-8

Julia admite completamente caracteres y cadenas Unicode. Como [discussed above](@ref man-characters), en literales de caracteres, los puntos de código Unicode se pueden representar utilizando las secuencias de escape Unicode `\u` y `\U`, así como todas las secuencias de escape estándar de C. Estas también se pueden utilizar para escribir literales de cadena:

```jldoctest unicodestring
julia> s = "\u2200 x \u2203 y"
"∀ x ∃ y"
```

Si estos caracteres Unicode se muestran como escapes o como caracteres especiales depende de la configuración regional de su terminal y su soporte para Unicode. Los literales de cadena se codifican utilizando la codificación UTF-8. UTF-8 es una codificación de ancho variable, lo que significa que no todos los caracteres se codifican en el mismo número de bytes ("unidades de código"). En UTF-8, los caracteres ASCII —es decir, aquellos con puntos de código menores que 0x80 (128)— se codifican tal como están en ASCII, utilizando un solo byte, mientras que los puntos de código 0x80 y superiores se codifican utilizando múltiples bytes —hasta cuatro por carácter.

Los índices de cadena en Julia se refieren a unidades de código (= bytes para UTF-8), los bloques de construcción de ancho fijo que se utilizan para codificar caracteres arbitrarios (puntos de código). Esto significa que no cada índice en una `String` es necesariamente un índice válido para un carácter. Si indexas en una cadena en un índice de byte inválido, se lanza un error:

```jldoctest unicodestring
julia> s[1]
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> s[2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[3]
ERROR: StringIndexError: invalid index [3], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[4]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

En este caso, el carácter `∀` es un carácter de tres bytes, por lo que los índices 2 y 3 son inválidos y el índice del siguiente carácter es 4; este siguiente índice válido se puede calcular mediante [`nextind(s,1)`](@ref), y el siguiente índice después de eso mediante `nextind(s,4)` y así sucesivamente.

Dado que `end` siempre es el último índice válido en una colección, `end-1` hace referencia a un índice de byte inválido si el penúltimo carácter es multibyte.

```jldoctest unicodestring
julia> s[end-1]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)

julia> s[end-2]
ERROR: StringIndexError: invalid index [9], valid nearby indices [7]=>'∃', [10]=>' '
Stacktrace:
[...]

julia> s[prevind(s, end, 2)]
'∃': Unicode U+2203 (category Sm: Symbol, math)
```

El primer caso funciona, porque el último carácter `y` y el espacio son caracteres de un byte, mientras que `end-2` indexa en medio de la representación multibyte de `∃`. La forma correcta para este caso es usar `prevind(s, lastindex(s), 2)` o, si estás usando ese valor para indexar en `s`, puedes escribir `s[prevind(s, end, 2)]` y `end` se expande a `lastindex(s)`.

La extracción de una subcadena utilizando la indexación por rango también espera índices de bytes válidos o se lanza un error:

```jldoctest unicodestring
julia> s[1:1]
"∀"

julia> s[1:2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[1:4]
"∀ "
```

Debido a las codificaciones de longitud variable, el número de caracteres en una cadena (dado por [`length(s)`](@ref)) no siempre es el mismo que el último índice. Si iteras a través de los índices del 1 al [`lastindex(s)`](@ref) e indexas en `s`, la secuencia de caracteres devuelta cuando no se lanzan errores es la secuencia de caracteres que componen la cadena `s`. Así, `length(s) <= lastindex(s)`, ya que cada carácter en una cadena debe tener su propio índice. La siguiente es una forma ineficiente y verbosa de iterar a través de los caracteres de `s`:

```jldoctest unicodestring
julia> for i = firstindex(s):lastindex(s)
           try
               println(s[i])
           catch
               # ignore the index error
           end
       end
∀

x

∃

y
```

Las líneas en blanco en realidad tienen espacios en ellas. Afortunadamente, el extraño modismo anterior es innecesario para iterar a través de los caracteres en una cadena, ya que puedes usar la cadena como un objeto iterable, sin necesidad de manejo de excepciones:

```jldoctest unicodestring
julia> for c in s
           println(c)
       end
∀

x

∃

y
```

Si necesitas obtener índices válidos para una cadena, puedes usar las funciones [`nextind`](@ref) y [`prevind`](@ref) para incrementar/decrementar al siguiente/anterior índice válido, como se mencionó anteriormente. También puedes usar la función [`eachindex`](@ref) para iterar sobre los índices de caracteres válidos:

```jldoctest unicodestring
julia> collect(eachindex(s))
7-element Vector{Int64}:
  1
  4
  5
  6
  7
 10
 11
```

Para acceder a las unidades de código en bruto (bytes para UTF-8) de la codificación, puedes usar la función [`codeunit(s,i)`](@ref), donde el índice `i` se ejecuta de manera consecutiva desde `1` hasta [`ncodeunits(s)`](@ref). La función [`codeunits(s)`](@ref) devuelve un envoltorio `AbstractVector{UInt8}` que te permite acceder a estas unidades de código en bruto (bytes) como un arreglo.

Las cadenas en Julia pueden contener secuencias de unidades de código UTF-8 no válidas. Esta convención permite tratar cualquier secuencia de bytes como una `String`. En tales situaciones, una regla es que al analizar una secuencia de unidades de código de izquierda a derecha, los caracteres se forman a partir de la secuencia más larga de unidades de código de 8 bits que coincide con el inicio de uno de los siguientes patrones de bits (cada `x` puede ser `0` o `1`):

  * `0xxxxxxx`;
  * `110xxxxx` `10xxxxxx`;
  * `1110xxxx` `10xxxxxx` `10xxxxxx`;
  * `11110xxx` `10xxxxxx` `10xxxxxx` `10xxxxxx`;
  * `10xxxxxx`;
  * `11111xxx`.

En particular, esto significa que las secuencias de unidades de código demasiado largas y demasiado altas, así como sus prefijos, se tratan como un solo carácter inválido en lugar de múltiples caracteres inválidos. Esta regla puede explicarse mejor con un ejemplo:

```julia-repl
julia> s = "\xc0\xa0\xe2\x88\xe2|"
"\xc0\xa0\xe2\x88\xe2|"

julia> foreach(display, s)
'\xc0\xa0': [overlong] ASCII/Unicode U+0020 (category Zs: Separator, space)
'\xe2\x88': Malformed UTF-8 (category Ma: Malformed, bad data)
'\xe2': Malformed UTF-8 (category Ma: Malformed, bad data)
'|': ASCII/Unicode U+007C (category Sm: Symbol, math)

julia> isvalid.(collect(s))
4-element BitArray{1}:
 0
 0
 0
 1

julia> s2 = "\xf7\xbf\xbf\xbf"
"\U1fffff"

julia> foreach(display, s2)
'\U1fffff': Unicode U+1FFFFF (category In: Invalid, too high)
```

Podemos ver que las dos primeras unidades de código en la cadena `s` forman una codificación excesiva del carácter de espacio. Es inválido, pero se acepta en una cadena como un solo carácter. Las siguientes dos unidades de código forman un inicio válido de una secuencia UTF-8 de tres bytes. Sin embargo, la quinta unidad de código `\xe2` no es su continuación válida. Por lo tanto, las unidades de código 3 y 4 también se interpretan como caracteres malformados en esta cadena. De manera similar, la unidad de código 5 forma un carácter malformado porque `|` no es una continuación válida para él. Finalmente, la cadena `s2` contiene un punto de código demasiado alto.

Julia utiliza la codificación UTF-8 por defecto, y el soporte para nuevas codificaciones se puede agregar mediante paquetes. Por ejemplo, el paquete [LegacyStrings.jl](https://github.com/JuliaStrings/LegacyStrings.jl) implementa los tipos `UTF16String` y `UTF32String`. La discusión adicional sobre otras codificaciones y cómo implementar soporte para ellas está más allá del alcance de este documento por el momento. Para una discusión más detallada sobre los problemas de codificación UTF-8, consulte la sección a continuación sobre [byte array literals](@ref man-byte-array-literals). La función [`transcode`](@ref) se proporciona para convertir datos entre las diversas codificaciones UTF-xx, principalmente para trabajar con datos y bibliotecas externas.

## [Concatenation](@id man-concatenation)

Una de las operaciones de cadena más comunes y útiles es la concatenación:

```jldoctest stringconcat
julia> greet = "Hello"
"Hello"

julia> whom = "world"
"world"

julia> string(greet, ", ", whom, ".\n")
"Hello, world.\n"
```

Es importante estar consciente de situaciones potencialmente peligrosas, como la concatenación de cadenas UTF-8 no válidas. La cadena resultante puede contener caracteres diferentes a las cadenas de entrada, y su número de caracteres puede ser menor que la suma de los números de caracteres de las cadenas concatenadas, por ejemplo:

```julia-repl
julia> a, b = "\xe2\x88", "\x80"
("\xe2\x88", "\x80")

julia> c = string(a, b)
"∀"

julia> collect.([a, b, c])
3-element Vector{Vector{Char}}:
 ['\xe2\x88']
 ['\x80']
 ['∀']

julia> length.([a, b, c])
3-element Vector{Int64}:
 1
 1
 1
```

Esta situación solo puede ocurrir para cadenas UTF-8 no válidas. Para cadenas UTF-8 válidas, la concatenación preserva todos los caracteres en las cadenas y la aditividad de las longitudes de las cadenas.

Julia también proporciona [`*`](@ref) para la concatenación de cadenas:

```jldoctest stringconcat
julia> greet * ", " * whom * ".\n"
"Hello, world.\n"
```

Mientras que `*` puede parecer una elección sorprendente para los usuarios de lenguajes que proporcionan `+` para la concatenación de cadenas, este uso de `*` tiene precedentes en matemáticas, particularmente en álgebra abstracta.

En matemáticas, `+` generalmente denota una operación *conmutativa*, donde el orden de los operandos no importa. Un ejemplo de esto es la suma de matrices, donde `A + B == B + A` para cualquier matriz `A` y `B` que tengan la misma forma. En contraste, `*` típicamente denota una operación *no conmutativa*, donde el orden de los operandos *sí* importa. Un ejemplo de esto es la multiplicación de matrices, donde en general `A * B != B * A`. Al igual que con la multiplicación de matrices, la concatenación de cadenas es no conmutativa: `greet * whom != whom * greet`. Como tal, `*` es una elección más natural para un operador de concatenación de cadenas en infijo, consistente con el uso matemático común.

Más precisamente, el conjunto de todas las cadenas de longitud finita *S* junto con el operador de concatenación de cadenas `*` forma un [free monoid](https://en.wikipedia.org/wiki/Free_monoid) (*S*, `*`). El elemento identidad de este conjunto es la cadena vacía, `""`. Siempre que un monoid libre no sea conmutativo, la operación se representa típicamente como `\cdot`, `*`, o un símbolo similar, en lugar de `+`, que como se indicó generalmente implica conmutatividad.

## [Interpolation](@id string-interpolation)

Construir cadenas utilizando concatenación puede volverse un poco engorroso, sin embargo. Para reducir la necesidad de estas llamadas verbosas a [`string`](@ref) o multiplicaciones repetidas, Julia permite la interpolación en literales de cadena utilizando `$`, como en Perl:

```jldoctest
julia> greet = "Hello"; whom = "world";

julia> "$greet, $whom.\n"
"Hello, world.\n"
```

Esto es más legible y conveniente y equivalente a la concatenación de cadenas anterior: el sistema reescribe este aparente literal de cadena único en la llamada `string(greet, ", ", whom, ".\n")`.

La expresión completa más corta después del `$` se toma como la expresión cuyo valor se va a interpolar en la cadena. Así, puedes interpolar cualquier expresión en una cadena usando paréntesis:

```jldoctest
julia> "1 + 2 = $(1 + 2)"
"1 + 2 = 3"
```

Tanto la concatenación como la interpolación de cadenas llaman a [`string`](@ref) para convertir objetos en forma de cadena. Sin embargo, `string` en realidad solo devuelve la salida de [`print`](@ref), por lo que los nuevos tipos deberían agregar métodos a `4d61726b646f776e2e436f64652822222c20227072696e742229_40726566` o [`show`](@ref) en lugar de `string`.

La mayoría de los objetos que no son `AbstractString` se convierten en cadenas que corresponden estrechamente a cómo se ingresan como expresiones literales:

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> "v: $v"
"v: [1, 2, 3]"
```

[`string`](@ref) es la identidad para los valores `AbstractString` y `AbstractChar`, por lo que se interpolan en cadenas como ellos mismos, sin comillas ni escape:

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> "hi, $c"
"hi, x"
```

Para incluir un `$` literal en una cadena literal, escápalo con una barra invertida:

```jldoctest
julia> print("I have \$100 in my account.\n")
I have $100 in my account.
```

## Triple-Quoted String Literals

Cuando se crean cadenas utilizando comillas triples (`"""..."""`), tienen un comportamiento especial que puede ser útil para crear bloques de texto más largos.

Primero, las cadenas de texto entre comillas triples también se desindentan al nivel de la línea menos indentada. Esto es útil para definir cadenas dentro del código que está indentado. Por ejemplo:

```jldoctest
julia> str = """
           Hello,
           world.
         """
"  Hello,\n  world.\n"
```

En este caso, la línea final (vacía) antes del cierre `"""` establece el nivel de sangría.

El nivel de dedentación se determina como la secuencia común de inicio más larga de espacios o tabulaciones en todas las líneas, excluyendo la línea que sigue al `"""` de apertura y las líneas que contienen solo espacios o tabulaciones (la línea que contiene el `"""` de cierre siempre se incluye). Luego, para todas las líneas, excluyendo el texto que sigue al `"""` de apertura, se elimina la secuencia común de inicio (incluyendo líneas que contienen solo espacios y tabulaciones si comienzan con esta secuencia), por ejemplo:

```jldoctest
julia> """    This
         is
           a test"""
"    This\nis\n  a test"
```

A continuación, si el `"""` de apertura es seguido por una nueva línea, la nueva línea se elimina de la cadena resultante.

```julia
"""hello"""
```

es equivalente a

```julia
"""
hello"""
```

pero

```julia
"""

hello"""
```

will contain a literal newline at the beginning.

La eliminación de la nueva línea se realiza después de la dedentación. Por ejemplo:

```jldoctest
julia> """
         Hello,
         world."""
"Hello,\nworld."
```

Si se elimina la nueva línea utilizando una barra invertida, la dedentación también se respetará:

```jldoctest
julia> """
         Averylong\
         word"""
"Averylongword"
```

El espacio en blanco al final se deja sin alterar.

Las cadenas literales de triple comillas pueden contener caracteres `"` sin necesidad de escapar.

Tenga en cuenta que los saltos de línea en cadenas literales, ya sean entre comillas simples o triples, resultan en un carácter de nueva línea (LF) `\n` en la cadena, incluso si su editor utiliza un retorno de carro `\r` (CR) o una combinación CRLF para finalizar las líneas. Para incluir un CR en una cadena, use una secuencia de escape explícita `\r`; por ejemplo, puede ingresar la cadena literal `"a CRLF line ending\r\n"`.

## Common Operations

Puedes comparar cadenas lexicográficamente utilizando los operadores de comparación estándar:

```jldoctest
julia> "abracadabra" < "xylophone"
true

julia> "abracadabra" == "xylophone"
false

julia> "Hello, world." != "Goodbye, world."
true

julia> "1 + 2 = 3" == "1 + 2 = $(1 + 2)"
true
```

Puedes buscar el índice de un carácter particular utilizando las funciones [`findfirst`](@ref) y [`findlast`](@ref):

```jldoctest
julia> findfirst('o', "xylophone")
4

julia> findlast('o', "xylophone")
7

julia> findfirst('z', "xylophone")
```

Puedes comenzar la búsqueda de un carácter en un desplazamiento dado utilizando las funciones [`findnext`](@ref) y [`findprev`](@ref):

```jldoctest
julia> findnext('o', "xylophone", 1)
4

julia> findnext('o', "xylophone", 5)
7

julia> findprev('o', "xylophone", 5)
4

julia> findnext('o', "xylophone", 8)
```

Puedes usar la función [`occursin`](@ref) para verificar si una subcadena se encuentra dentro de una cadena:

```jldoctest
julia> occursin("world", "Hello, world.")
true

julia> occursin("o", "Xylophon")
true

julia> occursin("a", "Xylophon")
false

julia> occursin('o', "Xylophon")
true
```

El último ejemplo muestra que [`occursin`](@ref) también puede buscar un literal de carácter.

Dos otras funciones de cadena útiles son [`repeat`](@ref) y [`join`](@ref):

```jldoctest
julia> repeat(".:Z:.", 10)
".:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:."

julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"
```

Algunas otras funciones útiles incluyen:

  * [`firstindex(str)`](@ref) da el índice mínimo (byte) que se puede usar para indexar en `str` (siempre 1 para cadenas, no necesariamente cierto para otros contenedores).
  * [`lastindex(str)`](@ref) da el índice (byte) máximo que se puede usar para indexar en `str`.
  * [`length(str)`](@ref) the number of characters in `str`.
  * [`length(str, i, j)`](@ref) el número de índices de caracteres válidos en `str` desde `i` hasta `j`.
  * [`ncodeunits(str)`](@ref) número de [code units](https://en.wikipedia.org/wiki/Character_encoding#Terminology) en una cadena.
  * [`codeunit(str, i)`](@ref) devuelve el valor de la unidad de código en la cadena `str` en el índice `i`.
  * [`thisind(str, i)`](@ref) dado un índice arbitrario en una cadena, encuentra el primer índice del carácter al que apunta el índice.
  * [`nextind(str, i, n=1)`](@ref) encuentra el inicio del `n`-ésimo carácter comenzando después del índice `i`.
  * [`prevind(str, i, n=1)`](@ref) encuentra el inicio del `n`-ésimo carácter comenzando antes del índice `i`.

## [Non-Standard String Literals](@id non-standard-string-literals)

Hay situaciones en las que deseas construir una cadena o usar semántica de cadena, pero el comportamiento de la construcción de cadena estándar no es exactamente lo que se necesita. Para este tipo de situaciones, Julia proporciona literales de cadena no estándar. Un literal de cadena no estándar se parece a un literal de cadena entre comillas dobles regular, pero está inmediatamente precedido por un identificador y puede comportarse de manera diferente a un literal de cadena normal.

[Regular expressions](@ref man-regex-literals), [byte array literals](@ref man-byte-array-literals), y [version number literals](@ref man-version-number-literals), como se describe a continuación, son algunos ejemplos de literales de cadena no estándar. Los usuarios y paquetes también pueden definir nuevos literales de cadena no estándar. Se proporciona más documentación en la sección [Metaprogramming](@ref meta-non-standard-string-literals).

## [Regular Expressions](@id man-regex-literals)

A veces no estás buscando una cadena exacta, sino un *patrón* particular. Por ejemplo, supongamos que estás tratando de extraer una sola fecha de un gran archivo de texto. No sabes cuál es esa fecha (por eso la estás buscando), pero sí sabes que se verá algo así como `YYYY-MM-DD`. Las expresiones regulares te permiten especificar estos patrones y buscarlos.

Julia utiliza la versión 2 de expresiones regulares compatibles con Perl (regexes), como lo proporciona la [PCRE](https://www.pcre.org/) biblioteca (ver la [PCRE2 syntax description](https://www.pcre.org/current/doc/html/pcre2syntax.html) para más detalles). Las expresiones regulares están relacionadas con las cadenas de dos maneras: la conexión obvia es que las expresiones regulares se utilizan para encontrar patrones regulares en las cadenas; la otra conexión es que las expresiones regulares se ingresan como cadenas, que se analizan en una máquina de estados que se puede utilizar para buscar patrones en las cadenas de manera eficiente. En Julia, las expresiones regulares se ingresan utilizando literales de cadena no estándar precedidos por varios identificadores que comienzan con `r`. El literal de expresión regular más básico sin ninguna opción activada simplemente utiliza `r"..."`:

```jldoctest
julia> re = r"^\s*(?:#|$)"
r"^\s*(?:#|$)"

julia> typeof(re)
Regex
```

Para verificar si una expresión regular coincide con una cadena, usa [`occursin`](@ref):

```jldoctest
julia> occursin(r"^\s*(?:#|$)", "not a comment")
false

julia> occursin(r"^\s*(?:#|$)", "# a comment")
true
```

Como se puede ver aquí, [`occursin`](@ref) simplemente devuelve verdadero o falso, indicando si hay una coincidencia para la expresión regular dada en la cadena. Sin embargo, comúnmente, uno quiere saber no solo si una cadena coincidió, sino también *cómo* coincidió. Para capturar esta información sobre una coincidencia, utiliza la función [`match`](@ref) en su lugar:

```jldoctest
julia> match(r"^\s*(?:#|$)", "not a comment")

julia> match(r"^\s*(?:#|$)", "# a comment")
RegexMatch("#")
```

Si la expresión regular no coincide con la cadena dada, [`match`](@ref) devuelve [`nothing`](@ref) – un valor especial que no imprime nada en el prompt interactivo. Aparte de no imprimir, es un valor completamente normal y puedes probarlo programáticamente:

```julia
m = match(r"^\s*(?:#|$)", line)
if m === nothing
    println("not a comment")
else
    println("blank or comment")
end
```

Si una expresión regular coincide, el valor devuelto por [`match`](@ref) es un objeto [`RegexMatch`](@ref). Estos objetos registran cómo coincide la expresión, incluyendo la subcadena que coincide con el patrón y cualquier subcadena capturada, si las hay. Este ejemplo solo captura la porción de la subcadena que coincide, pero quizás queramos capturar cualquier texto no en blanco después del carácter de comentario. Podríamos hacer lo siguiente:

```jldoctest
julia> m = match(r"^\s*(?:#\s*(.*?)\s*$)", "# a comment ")
RegexMatch("# a comment ", 1="a comment")
```

Al llamar a [`match`](@ref), tienes la opción de especificar un índice en el que comenzar la búsqueda. Por ejemplo:

```jldoctest
julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",1)
RegexMatch("1")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",6)
RegexMatch("2")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",11)
RegexMatch("3")
```

Puedes extraer la siguiente información de un objeto `RegexMatch`:

  * la subcadena completa coincidente: `m.match`
  * las subcadenas capturadas como un arreglo de cadenas: `m.captures`
  * el desplazamiento en el que comienza todo el partido: `m.offset`
  * los desplazamientos de las subcadenas capturadas como un vector: `m.offsets`

Para cuando una captura no coincide, en lugar de una subcadena, `m.captures` contiene `nothing` en esa posición, y `m.offsets` tiene un desplazamiento cero (recuerda que los índices en Julia son basados en 1, por lo que un desplazamiento cero en una cadena es inválido). Aquí hay un par de ejemplos algo forzados:

```jldoctest acdmatch
julia> m = match(r"(a|b)(c)?(d)", "acd")
RegexMatch("acd", 1="a", 2="c", 3="d")

julia> m.match
"acd"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 "c"
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 2
 3

julia> m = match(r"(a|b)(c)?(d)", "ad")
RegexMatch("ad", 1="a", 2=nothing, 3="d")

julia> m.match
"ad"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 nothing
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 0
 2
```

Es conveniente tener las capturas devueltas como un array para que se pueda usar la sintaxis de desestructuración para enlazarlas a variables locales. Como una conveniencia, el objeto `RegexMatch` implementa métodos de iterador que pasan al campo `captures`, por lo que puedes desestructurar el objeto de coincidencia directamente:

```jldoctest acdmatch
julia> first, second, third = m; first
"a"
```

Las capturas también se pueden acceder indexando el objeto `RegexMatch` con el número o el nombre del grupo de captura:

```jldoctest
julia> m=match(r"(?<hour>\d+):(?<minute>\d+)","12:45")
RegexMatch("12:45", hour="12", minute="45")

julia> m[:minute]
"45"

julia> m[2]
"45"
```

Las capturas se pueden referenciar en una cadena de sustitución al usar [`replace`](@ref) utilizando `\n` para referirse al enésimo grupo de captura y prefijando la cadena de sustitución con `s`. El grupo de captura 0 se refiere al objeto de coincidencia completo. Los grupos de captura nombrados se pueden referenciar en la sustitución con `\g<nombregrupo>`. Por ejemplo:

```jldoctest
julia> replace("first second", r"(\w+) (?<agroup>\w+)" => s"\g<agroup> \1")
"second first"
```

Los grupos de captura numerados también se pueden referenciar como `\g<n>` para desambiguación, como en:

```jldoctest
julia> replace("a", r"." => s"\g<0>1")
"a1"
```

Puedes modificar el comportamiento de las expresiones regulares mediante alguna combinación de las banderas `i`, `m`, `s` y `x` después de la marca de cierre de comillas dobles. Estas banderas tienen el mismo significado que en Perl, como se explica en este extracto de [perlre manpage](https://perldoc.perl.org/perlre#Modifiers):

```
i   Do case-insensitive pattern matching.

    If locale matching rules are in effect, the case map is taken
    from the current locale for code points less than 255, and
    from Unicode rules for larger code points. However, matches
    that would cross the Unicode rules/non-Unicode rules boundary
    (ords 255/256) will not succeed.

m   Treat string as multiple lines.  That is, change "^" and "$"
    from matching the start or end of the string to matching the
    start or end of any line anywhere within the string.

s   Treat string as single line.  That is, change "." to match any
    character whatsoever, even a newline, which normally it would
    not match.

    Used together, as r""ms, they let the "." match any character
    whatsoever, while still allowing "^" and "$" to match,
    respectively, just after and just before newlines within the
    string.

x   Tells the regular expression parser to ignore most whitespace
    that is neither backslashed nor within a character class. You
    can use this to break up your regular expression into
    (slightly) more readable parts. The '#' character is also
    treated as a metacharacter introducing a comment, just as in
    ordinary code.
```

Por ejemplo, la siguiente expresión regular tiene las tres banderas activadas:

```jldoctest
julia> r"a+.*b+.*d$"ism
r"a+.*b+.*d$"ims

julia> match(r"a+.*b+.*d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

El literal `r"..."` se construye sin interpolación y sin desescapado (excepto por la comilla `"` que aún debe ser escapada). Aquí hay un ejemplo que muestra la diferencia con los literales de cadena estándar:

```julia-repl
julia> x = 10
10

julia> r"$x"
r"$x"

julia> "$x"
"10"

julia> r"\x"
r"\x"

julia> "\x"
ERROR: syntax: invalid escape sequence
```

Las cadenas de regex con comillas triples, de la forma `r"""..."""`, también son compatibles (y pueden ser convenientes para expresiones regulares que contienen comillas o saltos de línea).

El constructor `Regex()` se puede utilizar para crear una cadena regex válida de manera programática. Esto permite usar el contenido de variables de cadena y otras operaciones de cadena al construir la cadena regex. Cualquiera de los códigos regex anteriores se puede usar dentro del argumento de cadena única para `Regex()`. Aquí hay algunos ejemplos:

```jldoctest
julia> using Dates

julia> d = Date(1962,7,10)
1962-07-10

julia> regex_d = Regex("Day " * string(day(d)))
r"Day 10"

julia> match(regex_d, "It happened on Day 10")
RegexMatch("Day 10")

julia> name = "Jon"
"Jon"

julia> regex_name = Regex("[\"( ]\\Q$name\\E[\") ]")  # interpolate value of name
r"[\"( ]\QJon\E[\") ]"

julia> match(regex_name, " Jon ")
RegexMatch(" Jon ")

julia> match(regex_name, "[Jon]") === nothing
true
```

Nota el uso de la secuencia de escape `\Q...\E`. Todos los caracteres entre `\Q` y `\E` se interpretan como caracteres literales. Esto es conveniente para hacer coincidir caracteres que de otro modo serían metacaracteres de regex. Sin embargo, se necesita precaución al usar esta característica junto con la interpolación de cadenas, ya que la cadena interpolada podría contener la secuencia `\E`, terminando inesperadamente la coincidencia literal. Las entradas del usuario deben ser saneadas antes de su inclusión en un regex.

## [Byte Array Literals](@id man-byte-array-literals)

Otro literal de cadena no estándar útil es el literal de cadena de matriz de bytes: `b"..."`. Esta forma te permite usar la notación de cadena para expresar matrices de bytes literales de solo lectura, es decir, matrices de valores [`UInt8`](@ref). El tipo de esos objetos es `CodeUnits{UInt8, String}`. Las reglas para los literales de matriz de bytes son las siguientes:

  * Los caracteres ASCII y las secuencias de escape ASCII producen un solo byte.
  * `\x` y las secuencias de escape octales producen el *byte* correspondiente al valor de escape.
  * Las secuencias de escape Unicode producen una secuencia de bytes que codifica ese punto de código en UTF-8.

Hay cierta superposición entre estas reglas, ya que el comportamiento de `\x` y las secuencias octales menores de 0x80 (128) están cubiertas por ambas de las dos primeras reglas, pero aquí estas reglas están de acuerdo. Juntas, estas reglas permiten usar fácilmente caracteres ASCII, valores de bytes arbitrarios y secuencias UTF-8 para producir arreglos de bytes. Aquí hay un ejemplo que utiliza los tres:

```jldoctest
julia> b"DATA\xff\u2200"
8-element Base.CodeUnits{UInt8, String}:
 0x44
 0x41
 0x54
 0x41
 0xff
 0xe2
 0x88
 0x80
```

La cadena ASCII "DATA" corresponde a los bytes 68, 65, 84, 65. `\xff` produce el único byte 255. La secuencia de escape Unicode `\u2200` se codifica en UTF-8 como los tres bytes 226, 136, 128. Tenga en cuenta que el arreglo de bytes resultante no corresponde a una cadena UTF-8 válida:

```jldoctest
julia> isvalid("DATA\xff\u2200")
false
```

Como se mencionó, el tipo `CodeUnits{UInt8, String}` se comporta como un arreglo de solo lectura de `UInt8` y si necesitas un vector estándar, puedes convertirlo usando `Vector{UInt8}`:

```jldoctest
julia> x = b"123"
3-element Base.CodeUnits{UInt8, String}:
 0x31
 0x32
 0x33

julia> x[1]
0x31

julia> x[1] = 0x32
ERROR: CanonicalIndexError: setindex! not defined for Base.CodeUnits{UInt8, String}
[...]

julia> Vector{UInt8}(x)
3-element Vector{UInt8}:
 0x31
 0x32
 0x33
```

También observa la distinción significativa entre `\xff` y `\uff`: la primera secuencia de escape codifica el *byte 255*, mientras que la última secuencia de escape representa el *punto de código 255*, que se codifica como dos bytes en UTF-8:

```jldoctest
julia> b"\xff"
1-element Base.CodeUnits{UInt8, String}:
 0xff

julia> b"\uff"
2-element Base.CodeUnits{UInt8, String}:
 0xc3
 0xbf
```

Los literales de caracteres utilizan el mismo comportamiento.

Para los puntos de código menores que `\u80`, sucede que la codificación UTF-8 de cada punto de código es simplemente el único byte producido por la correspondiente escape `\x`, por lo que la distinción se puede ignorar de manera segura. Sin embargo, para las escapes `\x80` a `\xff` en comparación con `\u80` a `\uff`, hay una diferencia importante: las primeras escapes codifican todos bytes individuales, que – a menos que sean seguidos por bytes de continuación muy específicos – no forman datos válidos en UTF-8, mientras que las últimas escapes representan todos los puntos de código Unicode con codificaciones de dos bytes.

Si esto es extremadamente confuso, intenta leer ["The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets"](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/). Es una excelente introducción a Unicode y UTF-8, y puede ayudar a aliviar algo de confusión sobre el tema.

## [Version Number Literals](@id man-version-number-literals)

Los números de versión se pueden expresar fácilmente con literales de cadena no estándar de la forma [`v"..."`](@ref @v_str). Los literales de número de versión crean objetos [`VersionNumber`](@ref) que siguen las especificaciones de [semantic versioning](https://semver.org/), y por lo tanto están compuestos de valores numéricos mayor, menor y de parche, seguidos de anotaciones alfanuméricas de pre-lanzamiento y de compilación. Por ejemplo, `v"0.2.1-rc1+win64"` se descompone en versión mayor `0`, versión menor `2`, versión de parche `1`, pre-lanzamiento `rc1` y compilación `win64`. Al ingresar un literal de versión, todo excepto el número de versión mayor es opcional, por lo tanto, por ejemplo, `v"0.2"` es equivalente a `v"0.2.0"` (con anotaciones de pre-lanzamiento/compilación vacías), `v"2"` es equivalente a `v"2.0.0"`, y así sucesivamente.

Los objetos `VersionNumber` son principalmente útiles para comparar fácilmente y correctamente dos (o más) versiones. Por ejemplo, la constante [`VERSION`](@ref) contiene el número de versión de Julia como un objeto `VersionNumber`, y por lo tanto se puede definir un comportamiento específico de la versión utilizando declaraciones simples como:

```julia
if v"0.2" <= VERSION < v"0.3-"
    # do something specific to 0.2 release series
end
```

Tenga en cuenta que en el ejemplo anterior se utiliza el número de versión no estándar `v"0.3-"`, con un `-` al final: esta notación es una extensión de Julia del estándar, y se utiliza para indicar una versión que es inferior a cualquier lanzamiento `0.3`, incluyendo todos sus pre-lanzamientos. Así que en el ejemplo anterior, el código solo se ejecutaría con versiones estables `0.2`, y excluiría versiones como `v"0.3.0-rc1"`. Para permitir también versiones inestables (es decir, pre-lanzamientos) `0.2`, la verificación del límite inferior debería modificarse así: `v"0.2-" <= VERSION`.

Otra extensión de especificación de versión no estándar permite usar un `+` al final para expresar un límite superior en las versiones de construcción, por ejemplo, `VERSION > v"0.2-rc1+"` se puede usar para significar cualquier versión por encima de `0.2-rc1` y cualquiera de sus construcciones: devolverá `false` para la versión `v"0.2-rc1+win64"` y `true` para `v"0.2-rc2"`.

Es una buena práctica utilizar tales versiones especiales en comparaciones (en particular, el `-` final siempre debe usarse en los límites superiores a menos que haya una buena razón para no hacerlo), pero no deben usarse como el número de versión real de nada, ya que son inválidas en el esquema de versionado semántico.

Además de ser utilizado para la constante [`VERSION`](@ref), los objetos `VersionNumber` se utilizan ampliamente en el módulo `Pkg` para especificar las versiones de los paquetes y sus dependencias.

## [Raw String Literals](@id man-raw-string-literals)

Las cadenas sin procesar sin interpolación ni desescapado se pueden expresar con literales de cadena no estándar de la forma `raw"..."`. Los literales de cadena sin procesar crean objetos `String` ordinarios que contienen el contenido encerrado exactamente como se ingresó, sin interpolación ni desescapado. Esto es útil para cadenas que contienen código o marcado en otros lenguajes que utilizan `$` o `\` como caracteres especiales.

La excepción es que las comillas aún deben ser escapadas, por ejemplo, `raw"\""` es equivalente a `"\""`. Para hacer posible expresar todas las cadenas, las barras invertidas también deben ser escapadas, pero solo cuando aparecen justo antes de un carácter de comillas:

```jldoctest
julia> println(raw"\\ \\\"")
\\ \"
```

Tenga en cuenta que los primeros dos barras invertidas aparecen textualmente en la salida, ya que no preceden a un carácter de comillas. Sin embargo, el siguiente carácter de barra invertida escapa la barra invertida que lo sigue, y la última barra invertida escapa una comilla, ya que estas barras invertidas aparecen antes de una comilla.

## [Annotated Strings](@id man-annotated-strings)

!!! note
    La API para AnnotatedStrings se considera experimental y está sujeta a cambios entre las versiones de Julia.


A veces es útil poder mantener metadatos relacionados con regiones de una cadena. Un [`AnnotatedString`](@ref Base.AnnotatedString) envuelve otra cadena y permite que las regiones de esta sean anotadas con valores etiquetados (`:label => value`). Todas las operaciones de cadena genéricas se aplican a la cadena subyacente. Sin embargo, cuando es posible, se preserva la información de estilo. Esto significa que puedes manipular un `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` —tomando subcadenas, rellenándolas, concatenándolas con otras cadenas— y las anotaciones de metadatos "vendrán junto con el viaje".

Este tipo de cadena es fundamental para el [StyledStrings stdlib](@ref stdlib-styledstrings), que utiliza anotaciones etiquetadas con `:face` para mantener información de estilo.

Al concatenar un [`AnnotatedString`](@ref Base.AnnotatedString), asegúrate de usar [`annotatedstring`](@ref Base.annotatedstring) en lugar de [`string`](@ref) si deseas mantener las anotaciones de cadena.

```jldoctest
julia> str = Base.AnnotatedString("hello there",
               [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
Base.AnnotatedString{String}

julia> str2 = Base.AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> Base.annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == Base.annotatedstring(str, str2) # *-concatenation still works
true
```

Las anotaciones de un [`AnnotatedString`](@ref Base.AnnotatedString) se pueden acceder y modificar a través de las funciones [`annotations`](@ref Base.annotations) y [`annotate!`](@ref Base.annotate!).
