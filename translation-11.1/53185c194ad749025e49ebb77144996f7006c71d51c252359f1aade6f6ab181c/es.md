# [Variables](@id man-variables)

Una variable, en Julia, es un nombre asociado (o vinculado) a un valor. Es útil cuando deseas almacenar un valor (que obtuviste después de algún cálculo, por ejemplo) para su uso posterior. Por ejemplo:

```julia-repl
# Assign the value 10 to the variable x
julia> x = 10
10

# Doing math with x's value
julia> x + 1
11

# Reassign x's value
julia> x = 1 + 1
2

# You can assign values of other types, like strings of text
julia> x = "Hello World!"
"Hello World!"
```

Julia proporciona un sistema extremadamente flexible para nombrar variables. Los nombres de las variables son sensibles a mayúsculas y minúsculas, y no tienen un significado semántico (es decir, el lenguaje no tratará las variables de manera diferente según sus nombres).

```jldoctest
julia> x = 1.0
1.0

julia> y = -3
-3

julia> Z = "My string"
"My string"

julia> customary_phrase = "Hello world!"
"Hello world!"

julia> UniversalDeclarationOfHumanRightsStart = "人人生而自由，在尊严和权利上一律平等。"
"人人生而自由，在尊严和权利上一律平等。"
```

Los nombres Unicode (en codificación UTF-8) están permitidos:

```jldoctest
julia> δ = 0.00001
1.0e-5

julia> 안녕하세요 = "Hello"
"Hello"
```

En el REPL de Julia y en varios otros entornos de edición de Julia, puedes escribir muchos símbolos matemáticos Unicode escribiendo el nombre del símbolo LaTeX precedido por una barra invertida y luego presionando tab. Por ejemplo, el nombre de la variable `δ` se puede ingresar escribiendo `\delta`-*tab*, o incluso `α̂⁽²⁾` escribiendo `\alpha`-*tab*-`\hat`-*tab*-`\^(2)`-*tab*. (Si encuentras un símbolo en algún lugar, por ejemplo, en el código de otra persona, que no sabes cómo escribir, la ayuda del REPL te lo dirá: solo escribe `?` y luego pega el símbolo.)

Julia incluso te permitirá ocultar constantes y funciones exportadas existentes con locales (aunque no se recomienda para evitar confusiones potenciales):

```jldoctest; filter = r"with \d+ methods"
julia> pi = 3
3

julia> pi
3

julia> sqrt = 4
4

julia> length() = 5
length (generic function with 1 method)

julia> Base.length
length (generic function with 79 methods)
```

Sin embargo, si intentas redefinir una constante o función incorporada que ya está en uso, Julia te dará un error:

```jldoctest
julia> pi
π = 3.1415926535897...

julia> pi = 3
ERROR: cannot assign a value to imported variable Base.pi from module Main

julia> sqrt(100)
10.0

julia> sqrt = 4
ERROR: cannot assign a value to imported variable Base.sqrt from module Main
```

## [Allowed Variable Names](@id man-allowed-variable-names)

Los nombres de las variables deben comenzar con una letra (A-Z o a-z), un guion bajo, o un subconjunto de puntos de código Unicode mayores que 00A0; en particular, [Unicode character categories](https://www.fileformat.info/info/unicode/category/index.htm) Lu/Ll/Lt/Lm/Lo/Nl (letras), Sc/So (símbolos de moneda y otros símbolos), y algunos otros caracteres similares a letras (por ejemplo, un subconjunto de los símbolos matemáticos Sm) son permitidos. Los caracteres subsiguientes también pueden incluir ! y dígitos (0-9 y otros caracteres en las categorías Nd/No), así como otros puntos de código Unicode: diacríticos y otras marcas modificadoras (categorías Mn/Mc/Me/Sk), algunos conectores de puntuación (categoría Pc), comillas, y algunos otros caracteres.

Los operadores como `+` también son identificadores válidos, pero se analizan de manera especial. En algunos contextos, los operadores pueden usarse como variables; por ejemplo, `(+)` se refiere a la función de adición, y `(+) = f` la reasignará. La mayoría de los operadores infijos de Unicode (en la categoría Sm), como `⊕`, se analizan como operadores infijos y están disponibles para métodos definidos por el usuario (por ejemplo, puedes usar `const ⊗ = kron` para definir `⊗` como un producto de Kronecker infijo). Los operadores también pueden tener sufijos con marcas modificadoras, primas y sub/superíndices, por ejemplo, `+̂ₐ″` se analiza como un operador infijo con la misma precedencia que `+`. Se requiere un espacio entre un operador que termina con una letra de subíndice/superíndice y un nombre de variable subsiguiente. Por ejemplo, si `+ᵃ` es un operador, entonces `+ᵃx` debe escribirse como `+ᵃ x` para distinguirlo de `+ ᵃx` donde `ᵃx` es el nombre de la variable.

Una clase particular de nombres de variables es aquella que contiene solo guiones bajos. Estos identificadores son de solo escritura. Es decir, solo se les pueden asignar valores, que se descartan inmediatamente, y sus valores no se pueden utilizar de ninguna manera.

```julia-repl
julia> x, ___ = size([2 2; 1 1])
(2, 2)

julia> y = ___
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions

julia> println(___)
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions
```

The only explicitly disallowed names for variables are the names of the built-in [Keywords](@ref Keywords):

```julia-repl
julia> else = false
ERROR: syntax: unexpected "else"

julia> try = "No"
ERROR: syntax: unexpected "="
```

Algunos caracteres Unicode se consideran equivalentes en identificadores. Diferentes formas de ingresar caracteres combinados Unicode (por ejemplo, acentos) se tratan como equivalentes (específicamente, los identificadores de Julia son [NFC](https://en.wikipedia.org/wiki/Unicode_equivalence). Julia también incluye algunas equivalencias no estándar para caracteres que son visualmente similares y que se pueden ingresar fácilmente mediante algunos métodos de entrada. Los caracteres Unicode `ɛ` (U+025B: letra latina minúscula e abierta) y `µ` (U+00B5: signo micro) se tratan como equivalentes a las letras griegas correspondientes. El punto medio `·` (U+00B7) y el griego [interpunct](https://en.wikipedia.org/wiki/Interpunct) `·` (U+0387) se tratan ambos como el operador de punto matemático `⋅` (U+22C5). El signo menos `−` (U+2212) se considera equivalente al signo de guion `-` (U+002D).

## [Assignment expressions and assignment versus mutation](@id man-assignment-expressions)

Una asignación `variable = valor` "vincula" el nombre `variable` al `valor` calculado en el lado derecho, y toda la asignación es tratada por Julia como una expresión igual al `valor` del lado derecho. Esto significa que las asignaciones pueden ser *encadenadas* (el mismo `valor` asignado a múltiples variables con `variable1 = variable2 = valor`) o utilizadas en otras expresiones, y también es por eso que su resultado se muestra en el REPL como el valor del lado derecho. (En general, el REPL muestra el valor de cualquier expresión que evalúes.) Por ejemplo, aquí el valor `4` de `b = 2+2` se utiliza en otra operación aritmética y asignación:

```jldoctest
julia> a = (b = 2+2) + 3
7

julia> a
7

julia> b
4
```

Una confusión común es la distinción entre *asignación* (dar un nuevo "nombre" a un valor) y *mutación* (cambiar un valor). Si ejecutas `a = 2` seguido de `a = 3`, has cambiado el "nombre" `a` para referirse a un nuevo valor `3` … no has cambiado el número `2`, así que `2+2` seguirá dando `4` y no `6`! Esta distinción se vuelve más clara al tratar con tipos *mutables* como [arrays](@ref lib-arrays), cuyos contenidos *pueden* ser cambiados:

```jldoctest mutation_vs_rebind
julia> a = [1,2,3] # an array of 3 integers
3-element Vector{Int64}:
 1
 2
 3

julia> b = a   # both b and a are names for the same array!
3-element Vector{Int64}:
 1
 2
 3
```

Aquí, la línea `b = a` *no* hace una copia del arreglo `a`, simplemente vincula el nombre `b` al *mismo* arreglo `a`: tanto `b` como `a` "apuntan" a un arreglo `[1,2,3]` en la memoria. En contraste, una asignación `a[i] = value` *cambia* el *contenido* del arreglo, y el arreglo modificado será visible a través de ambos nombres `a` y `b`:

```jldoctest mutation_vs_rebind
julia> a[1] = 42     # change the first element
42

julia> a = 3.14159   # a is now the name of a different object
3.14159

julia> b   # b refers to the original array object, which has been mutated
3-element Vector{Int64}:
 42
  2
  3
```

Es decir, `a[i] = value` (un alias para [`setindex!`](@ref)) *muta* un objeto de matriz existente en memoria, accesible a través de `a` o `b`. Posteriormente, establecer `a = 3.14159` no cambia esta matriz, simplemente vincula `a` a un objeto diferente; la matriz sigue siendo accesible a través de `b`. Otra sintaxis común para mutar un objeto existente es `a.field = value` (un alias para [`setproperty!`](@ref)), que se puede usar para cambiar un [`mutable struct`](@ref). También hay mutación a través de la asignación por punto, por ejemplo `b .= 5:7` (que muta nuestra matriz `b` en su lugar para contener `[5,6,7]`), como parte de [vectorized "dot" syntax](@ref man-dot-operators) de Julia.

Cuando llamas a un [function](@ref man-functions) en Julia, se comporta como si *asignaras* los valores de los argumentos a nuevos nombres de variables correspondientes a los argumentos de la función, como se discutió en [Argument-Passing Behavior](@ref man-argument-passing).  (Por [convention](@ref man-punctuation), las funciones que mutan uno o más de sus argumentos tienen nombres que terminan con `!`.)

## Stylistic Conventions

Mientras Julia impone pocas restricciones sobre los nombres válidos, se ha vuelto útil adoptar las siguientes convenciones:

  * Los nombres de las variables están en minúsculas.
  * La separación de palabras puede indicarse con guiones bajos (`'_'`), pero se desaconseja el uso de guiones bajos a menos que el nombre sea difícil de leer de otra manera.
  * Los nombres de `Type`s y `Module`s comienzan con una letra mayúscula y la separación de palabras se muestra con camel case en lugar de guiones bajos.
  * Los nombres de `function`s y `macro`s están en minúsculas, sin guiones bajos.
  * Las funciones que escriben en sus argumentos tienen nombres que terminan en `!`. A veces se les llama funciones "mutantes" o "in situ" porque están destinadas a producir cambios en sus argumentos después de que se llama a la función, no solo a devolver un valor.

Para más información sobre las convenciones estilísticas, consulta el [Style Guide](@ref).
