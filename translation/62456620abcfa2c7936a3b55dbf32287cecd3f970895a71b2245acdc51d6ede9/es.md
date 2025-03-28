# Integers and Floating-Point Numbers

Los enteros y los valores de punto flotante son los bloques de construcción básicos de la aritmética y la computación. Las representaciones integradas de tales valores se llaman primitivas numéricas, mientras que las representaciones de enteros y números de punto flotante como valores inmediatos en el código se conocen como literales numéricos. Por ejemplo, `1` es un literal entero, mientras que `1.0` es un literal de punto flotante; sus representaciones binarias en memoria como objetos son primitivas numéricas.

Julia proporciona una amplia gama de tipos numéricos primitivos, y se definen un conjunto completo de operadores aritméticos y bit a bit, así como funciones matemáticas estándar sobre ellos. Estos se mapean directamente a tipos numéricos y operaciones que son soportados nativamente en computadoras modernas, lo que permite a Julia aprovechar al máximo los recursos computacionales. Además, Julia proporciona soporte de software para [Arbitrary Precision Arithmetic](@ref), que puede manejar operaciones sobre valores numéricos que no pueden ser representados de manera efectiva en representaciones de hardware nativas, pero a costa de un rendimiento relativamente más lento.

Los siguientes son los tipos numéricos primitivos de Julia:

  * **Tipos de enteros:**

| Type              | Signed? | Number of bits | Smallest value | Largest value |
|:----------------- |:------- |:-------------- |:-------------- |:------------- |
| [`Int8`](@ref)    | ✓       | 8              | -2^7           | 2^7 - 1       |
| [`UInt8`](@ref)   |         | 8              | 0              | 2^8 - 1       |
| [`Int16`](@ref)   | ✓       | 16             | -2^15          | 2^15 - 1      |
| [`UInt16`](@ref)  |         | 16             | 0              | 2^16 - 1      |
| [`Int32`](@ref)   | ✓       | 32             | -2^31          | 2^31 - 1      |
| [`UInt32`](@ref)  |         | 32             | 0              | 2^32 - 1      |
| [`Int64`](@ref)   | ✓       | 64             | -2^63          | 2^63 - 1      |
| [`UInt64`](@ref)  |         | 64             | 0              | 2^64 - 1      |
| [`Int128`](@ref)  | ✓       | 128            | -2^127         | 2^127 - 1     |
| [`UInt128`](@ref) |         | 128            | 0              | 2^128 - 1     |
| [`Bool`](@ref)    | N/A     | 8              | `false` (0)    | `true` (1)    |

  * **Tipos de punto flotante:**

| Type              | Precision                                                                      | Number of bits |
|:----------------- |:------------------------------------------------------------------------------ |:-------------- |
| [`Float16`](@ref) | [half](https://en.wikipedia.org/wiki/Half-precision_floating-point_format)     | 16             |
| [`Float32`](@ref) | [single](https://en.wikipedia.org/wiki/Single_precision_floating-point_format) | 32             |
| [`Float64`](@ref) | [double](https://en.wikipedia.org/wiki/Double_precision_floating-point_format) | 64             |

Además, el soporte completo para [Complex and Rational Numbers](@ref) se basa en estos tipos numéricos primitivos. Todos los tipos numéricos interoperan de manera natural sin necesidad de conversión explícita, gracias a un [type promotion system](@ref conversion-and-promotion) flexible y extensible por el usuario.

## Integers

Los enteros literales se representan de la manera estándar:

```jldoctest
julia> 1
1

julia> 1234
1234
```

El tipo predeterminado para un literal entero depende de si el sistema objetivo tiene una arquitectura de 32 bits o de 64 bits:

```julia-repl
# 32-bit system:
julia> typeof(1)
Int32

# 64-bit system:
julia> typeof(1)
Int64
```

La variable interna de Julia [`Sys.WORD_SIZE`](@ref) indica si el sistema objetivo es de 32 bits o de 64 bits:

```julia-repl
# 32-bit system:
julia> Sys.WORD_SIZE
32

# 64-bit system:
julia> Sys.WORD_SIZE
64
```

Julia también define los tipos `Int` y `UInt`, que son alias para los tipos de enteros nativos con signo y sin signo del sistema, respectivamente:

```julia-repl
# 32-bit system:
julia> Int
Int32
julia> UInt
UInt32

# 64-bit system:
julia> Int
Int64
julia> UInt
UInt64
```

Los literales enteros más grandes que no se pueden representar utilizando solo 32 bits pero que se pueden representar en 64 bits siempre crean enteros de 64 bits, independientemente del tipo de sistema:

```jldoctest
# 32-bit or 64-bit system:
julia> typeof(3000000000)
Int64
```

Los enteros sin signo se ingresan y se muestran utilizando el prefijo `0x` y los dígitos hexadecimales (base 16) `0-9a-f` (los dígitos en mayúscula `A-F` también funcionan para la entrada). El tamaño del valor sin signo se determina por el número de dígitos hexadecimales utilizados:

```jldoctest
julia> x = 0x1
0x01

julia> typeof(x)
UInt8

julia> x = 0x123
0x0123

julia> typeof(x)
UInt16

julia> x = 0x1234567
0x01234567

julia> typeof(x)
UInt32

julia> x = 0x123456789abcdef
0x0123456789abcdef

julia> typeof(x)
UInt64

julia> x = 0x11112222333344445555666677778888
0x11112222333344445555666677778888

julia> typeof(x)
UInt128
```

Este comportamiento se basa en la observación de que cuando se utilizan literales hexadecimales sin signo para valores enteros, normalmente se están utilizando para representar una secuencia de bytes numéricos fija, en lugar de solo un valor entero.

Los literales binarios y octales también son compatibles:

```jldoctest
julia> x = 0b10
0x02

julia> typeof(x)
UInt8

julia> x = 0o010
0x08

julia> typeof(x)
UInt8

julia> x = 0x00000000000000001111222233334444
0x00000000000000001111222233334444

julia> typeof(x)
UInt128
```

En cuanto a los literales hexadecimales, los literales binarios y octales producen tipos de enteros sin signo. El tamaño del elemento de datos binarios es el tamaño mínimo necesario, si el dígito inicial del literal no es `0`. En el caso de ceros a la izquierda, el tamaño se determina por el tamaño mínimo necesario para un literal, que tiene la misma longitud pero con el dígito inicial `1`. Esto significa que:

  * `0x1` y `0x12` son literales `UInt8`,
  * `0x123` y `0x1234` son literales `UInt16`,
  * `0x12345` y `0x12345678` son literales `UInt32`,
  * `0x123456789` y `0x1234567890adcdef` son literales `UInt64`, etc.

Incluso si hay dígitos cero a la izquierda que no contribuyen al valor, cuentan para determinar el tamaño de almacenamiento de un literal. Así que `0x01` es un `UInt8` mientras que `0x0001` es un `UInt16`.

Eso permite al usuario controlar el tamaño.

Los literales sin signo (que comienzan con `0x`) que codifican enteros demasiado grandes para ser representados como valores `UInt128` construirán valores `BigInt` en su lugar. Este no es un tipo sin signo, pero es el único tipo incorporado lo suficientemente grande como para representar tales valores enteros grandes.

Los literales binarios, octales y hexadecimales pueden ser firmados por un `-` que precede inmediatamente al literal sin signo. Producen un entero sin signo del mismo tamaño que lo haría el literal sin signo, con el complemento a dos del valor:

```jldoctest
julia> -0x2
0xfe

julia> -0x0002
0xfffe
```

Los valores mínimo y máximo representables de tipos numéricos primitivos como los enteros se dan por las funciones [`typemin`](@ref) y [`typemax`](@ref):

```jldoctest
julia> (typemin(Int32), typemax(Int32))
(-2147483648, 2147483647)

julia> for T in [Int8,Int16,Int32,Int64,Int128,UInt8,UInt16,UInt32,UInt64,UInt128]
           println("$(lpad(T,7)): [$(typemin(T)),$(typemax(T))]")
       end
   Int8: [-128,127]
  Int16: [-32768,32767]
  Int32: [-2147483648,2147483647]
  Int64: [-9223372036854775808,9223372036854775807]
 Int128: [-170141183460469231731687303715884105728,170141183460469231731687303715884105727]
  UInt8: [0,255]
 UInt16: [0,65535]
 UInt32: [0,4294967295]
 UInt64: [0,18446744073709551615]
UInt128: [0,340282366920938463463374607431768211455]
```

Los valores devueltos por [`typemin`](@ref) y [`typemax`](@ref) son siempre del tipo de argumento dado. (La expresión anterior utiliza varias características que aún no se han introducido, incluyendo [for loops](@ref man-loops), [Strings](@ref man-strings), y [Interpolation](@ref string-interpolation), pero debería ser lo suficientemente fácil de entender para los usuarios con algo de experiencia en programación.)

### Overflow behavior

En Julia, exceder el valor máximo representable de un tipo dado resulta en un comportamiento de envoltura:

```jldoctest
julia> x = typemax(Int64)
9223372036854775807

julia> x + 1
-9223372036854775808

julia> x + 1 == typemin(Int64)
true
```

Las operaciones aritméticas con los tipos de enteros de Julia realizan inherentemente [modular arithmetic](https://en.wikipedia.org/wiki/Modular_arithmetic), reflejando las características de la aritmética entera en el hardware informático moderno. En escenarios donde el desbordamiento es una posibilidad, es crucial verificar explícitamente los efectos de envoltura que pueden resultar de tales desbordamientos. El módulo [`Base.Checked`](@ref) proporciona un conjunto de operaciones aritméticas equipadas con verificaciones de desbordamiento, que desencadenan errores si ocurre un desbordamiento. Para casos de uso donde el desbordamiento no puede ser tolerado bajo ninguna circunstancia, es aconsejable utilizar el tipo [`BigInt`](@ref), como se detalla en [Arbitrary Precision Arithmetic](@ref).

Un ejemplo del comportamiento de desbordamiento y cómo resolverlo potencialmente es el siguiente:

```jldoctest
julia> 10^19
-8446744073709551616

julia> big(10)^19
10000000000000000000
```

### Division errors

La división entera (la función `div`) tiene dos casos excepcionales: dividir por cero y dividir el número negativo más bajo ([`typemin`](@ref)) por -1. Ambos de estos casos lanzan un [`DivideError`](@ref). Las funciones de resto y módulo (`rem` y `mod`) lanzan un `4d61726b646f776e2e436f64652822222c20224469766964654572726f722229_40726566` cuando su segundo argumento es cero.

## Floating-Point Numbers

Los números de punto flotante literales se representan en los formatos estándar, utilizando [E-notation](https://en.wikipedia.org/wiki/Scientific_notation#E_notation) cuando sea necesario:

```jldoctest
julia> 1.0
1.0

julia> 1.
1.0

julia> 0.5
0.5

julia> .5
0.5

julia> -1.23
-1.23

julia> 1e10
1.0e10

julia> 2.5e-4
0.00025
```

Los resultados anteriores son todos valores [`Float64`](@ref). Los valores literales [`Float32`](@ref) se pueden ingresar escribiendo una `f` en lugar de `e`:

```jldoctest
julia> x = 0.5f0
0.5f0

julia> typeof(x)
Float32

julia> 2.5f-4
0.00025f0
```

Los valores se pueden convertir a [`Float32`](@ref) fácilmente:

```jldoctest
julia> x = Float32(-1.5)
-1.5f0

julia> typeof(x)
Float32
```

Los literales de punto flotante hexadecimal también son válidos, pero solo como [`Float64`](@ref) valores, con `p` precediendo el exponente en base 2:

```jldoctest
julia> 0x1p0
1.0

julia> 0x1.8p3
12.0

julia> x = 0x.4p-1
0.125

julia> typeof(x)
Float64
```

Los números de punto flotante de media precisión también son compatibles ([`Float16`](@ref)), pero se implementan en software y utilizan [`Float32`](@ref) para cálculos.

```jldoctest
julia> sizeof(Float16(4.))
2

julia> 2*Float16(4.)
Float16(8.0)
```

El guion bajo `_` se puede usar como separador de dígitos:

```jldoctest
julia> 10_000, 0.000_000_005, 0xdead_beef, 0b1011_0010
(10000, 5.0e-9, 0xdeadbeef, 0xb2)
```

### Floating-point zero

Los números de punto flotante tienen [two zeros](https://en.wikipedia.org/wiki/Signed_zero), cero positivo y cero negativo. Son iguales entre sí, pero tienen diferentes representaciones binarias, como se puede ver utilizando la función [`bitstring`](@ref):

```jldoctest
julia> 0.0 == -0.0
true

julia> bitstring(0.0)
"0000000000000000000000000000000000000000000000000000000000000000"

julia> bitstring(-0.0)
"1000000000000000000000000000000000000000000000000000000000000000"
```

### Special floating-point values

Hay tres valores de punto flotante estándar especificados que no corresponden a ningún punto en la recta numérica real:

| `Float16` | `Float32` | `Float64` | Name              | Description                                                     |
|:--------- |:--------- |:--------- |:----------------- |:--------------------------------------------------------------- |
| `Inf16`   | `Inf32`   | `Inf`     | positive infinity | a value greater than all finite floating-point values           |
| `-Inf16`  | `-Inf32`  | `-Inf`    | negative infinity | a value less than all finite floating-point values              |
| `NaN16`   | `NaN32`   | `NaN`     | not a number      | a value not `==` to any floating-point value (including itself) |

Para una discusión más detallada sobre cómo se ordenan estos valores de punto flotante no finitos entre sí y con respecto a otros flotantes, consulte [Numeric Comparisons](@ref). A través de [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008), estos valores de punto flotante son el resultado de ciertas operaciones aritméticas:

```jldoctest
julia> 1/Inf
0.0

julia> 1/0
Inf

julia> -5/0
-Inf

julia> 0.000001/0
Inf

julia> 0/0
NaN

julia> 500 + Inf
Inf

julia> 500 - Inf
-Inf

julia> Inf + Inf
Inf

julia> Inf - Inf
NaN

julia> Inf * Inf
Inf

julia> Inf / Inf
NaN

julia> 0 * Inf
NaN

julia> NaN == NaN
false

julia> NaN != NaN
true

julia> NaN < NaN
false

julia> NaN > NaN
false
```

Las funciones [`typemin`](@ref) y [`typemax`](@ref) también se aplican a tipos de punto flotante:

```jldoctest
julia> (typemin(Float16),typemax(Float16))
(-Inf16, Inf16)

julia> (typemin(Float32),typemax(Float32))
(-Inf32, Inf32)

julia> (typemin(Float64),typemax(Float64))
(-Inf, Inf)
```

### Machine epsilon

La mayoría de los números reales no pueden ser representados exactamente con números de punto flotante, por lo que para muchos propósitos es importante conocer la distancia entre dos números de punto flotante representables adyacentes, que a menudo se conoce como [machine epsilon](https://en.wikipedia.org/wiki/Machine_epsilon).

Julia proporciona [`eps`](@ref), que da la distancia entre `1.0` y el siguiente valor de punto flotante representable más grande:

```jldoctest
julia> eps(Float32)
1.1920929f-7

julia> eps(Float64)
2.220446049250313e-16

julia> eps() # same as eps(Float64)
2.220446049250313e-16
```

Estos valores son `2.0^-23` y `2.0^-52` como [`Float32`](@ref) y [`Float64`](@ref), respectivamente. La función [`eps`](@ref) también puede tomar un valor de punto flotante como argumento y da la diferencia absoluta entre ese valor y el siguiente valor de punto flotante representable. Es decir, `eps(x)` produce un valor del mismo tipo que `x` tal que `x + eps(x)` es el siguiente valor de punto flotante representable mayor que `x`:

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(1000.)
1.1368683772161603e-13

julia> eps(1e-27)
1.793662034335766e-43

julia> eps(0.0)
5.0e-324
```

La distancia entre dos números de punto flotante representables adyacentes no es constante, sino que es menor para valores más pequeños y mayor para valores más grandes. En otras palabras, los números de punto flotante representables son más densos en la recta de los números reales cerca de cero, y se vuelven más escasos exponencialmente a medida que uno se aleja de cero. Por definición, `eps(1.0)` es lo mismo que `eps(Float64)` ya que `1.0` es un valor de punto flotante de 64 bits.

Julia también proporciona las funciones [`nextfloat`](@ref) y [`prevfloat`](@ref) que devuelven el siguiente número de punto flotante representable más grande o más pequeño al argumento, respectivamente:

```jldoctest
julia> x = 1.25f0
1.25f0

julia> nextfloat(x)
1.2500001f0

julia> prevfloat(x)
1.2499999f0

julia> bitstring(prevfloat(x))
"00111111100111111111111111111111"

julia> bitstring(x)
"00111111101000000000000000000000"

julia> bitstring(nextfloat(x))
"00111111101000000000000000000001"
```

Este ejemplo destaca el principio general de que los números de punto flotante representables adyacentes también tienen representaciones enteras binarias adyacentes.

### Rounding modes

Si un número no tiene una representación de punto flotante exacta, debe redondearse a un valor representable apropiado. Sin embargo, la forma en que se realiza este redondeo puede cambiarse si es necesario de acuerdo con los modos de redondeo presentados en el [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008).

El modo predeterminado utilizado es siempre [`RoundNearest`](@ref), que redondea al valor representable más cercano, con empates redondeados hacia el valor más cercano con un bit menos significativo par.

### Background and References

La aritmética de punto flotante implica muchas sutilezas que pueden sorprender a los usuarios que no están familiarizados con los detalles de implementación de bajo nivel. Sin embargo, estas sutilezas se describen en detalle en la mayoría de los libros sobre computación científica, y también en las siguientes referencias:

  * La guía definitiva sobre aritmética de punto flotante es el [IEEE 754-2008 Standard](https://standards.ieee.org/standard/754-2008.html); sin embargo, no está disponible de forma gratuita en línea.
  * Para una presentación breve pero clara de cómo se representan los números de punto flotante, consulte el [article](https://www.johndcook.com/blog/2009/04/06/anatomy-of-a-floating-point-number/) de John D. Cook sobre el tema, así como su [introduction](https://www.johndcook.com/blog/2009/04/06/numbers-are-a-leaky-abstraction/) sobre algunos de los problemas que surgen de cómo esta representación difiere en comportamiento de la abstracción idealizada de los números reales.
  * También se recomienda el [series of blog posts on floating-point numbers](https://randomascii.wordpress.com/2012/05/20/thats-not-normalthe-performance-of-odd-floats/).
  * Para una excelente y profunda discusión sobre los números de punto flotante y los problemas de precisión numérica que se encuentran al calcular con ellos, consulte el artículo de David Goldberg [What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.22.6768&rep=rep1&type=pdf).
  * Para una documentación aún más extensa sobre la historia de, la razón de ser y los problemas con los números de punto flotante, así como una discusión sobre muchos otros temas en computación numérica, consulte el [collected writings](https://people.eecs.berkeley.edu/~wkahan/) de [William Kahan](https://en.wikipedia.org/wiki/William_Kahan), comúnmente conocido como el "Padre del Punto Flotante". De particular interés puede ser [An Interview with the Old Man of Floating-Point](https://people.eecs.berkeley.edu/~wkahan/ieee754status/754story.html).

## Arbitrary Precision Arithmetic

Para permitir cálculos con enteros de precisión arbitraria y números de punto flotante, Julia envuelve el [GNU Multiple Precision Arithmetic Library (GMP)](https://gmplib.org) y el [GNU MPFR Library](https://www.mpfr.org), respectivamente. Los tipos [`BigInt`](@ref) y [`BigFloat`](@ref) están disponibles en Julia para enteros de precisión arbitraria y números de punto flotante, respectivamente.

Los constructores existen para crear estos tipos a partir de tipos numéricos primitivos, y el [string literal](@ref non-standard-string-literals) [`@big_str`](@ref) o [`parse`](@ref) se pueden usar para construirlos a partir de `AbstractString`s. Los `BigInt`s también se pueden ingresar como literales enteros cuando son demasiado grandes para otros tipos de enteros incorporados. Tenga en cuenta que, dado que no hay un tipo de entero de precisión arbitraria sin signo en `Base` (`BigInt` es suficiente en la mayoría de los casos), se pueden usar literales hexadecimales, octales y binarios (además de literales decimales).

Una vez creados, participan en aritmética con todos los demás tipos numéricos gracias a [type promotion and conversion mechanism](@ref conversion-and-promotion):

```jldoctest
julia> BigInt(typemax(Int64)) + 1
9223372036854775808

julia> big"123456789012345678901234567890" + 1
123456789012345678901234567891

julia> parse(BigInt, "123456789012345678901234567890") + 1
123456789012345678901234567891

julia> string(big"2"^200, base=16)
"100000000000000000000000000000000000000000000000000"

julia> 0x100000000000000000000000000000000-1 == typemax(UInt128)
true

julia> 0x000000000000000000000000000000000
0

julia> typeof(ans)
BigInt

julia> big"1.23456789012345678901"
1.234567890123456789010000000000000000000000000000000000000000000000000000000004

julia> parse(BigFloat, "1.23456789012345678901")
1.234567890123456789010000000000000000000000000000000000000000000000000000000004

julia> BigFloat(2.0^66) / 3
2.459565876494606882133333333333333333333333333333333333333333333333333333333344e+19

julia> factorial(BigInt(40))
815915283247897734345611269596115894272000000000
```

Sin embargo, la promoción de tipos entre los tipos primitivos mencionados y [`BigInt`](@ref)/[`BigFloat`](@ref) no es automática y debe ser declarada explícitamente.

```jldoctest
julia> x = typemin(Int64)
-9223372036854775808

julia> x = x - 1
9223372036854775807

julia> typeof(x)
Int64

julia> y = BigInt(typemin(Int64))
-9223372036854775808

julia> y = y - 1
-9223372036854775809

julia> typeof(y)
BigInt
```

La precisión predeterminada (en número de bits del significante) y el modo de redondeo de [`BigFloat`](@ref) se pueden cambiar globalmente llamando a [`setprecision`](@ref) y [`setrounding`](@ref), y todos los cálculos posteriores tendrán en cuenta estos cambios. Alternativamente, la precisión o el redondeo se pueden cambiar solo dentro de la ejecución de un bloque particular de código utilizando las mismas funciones con un bloque `do`:

```jldoctest
julia> setrounding(BigFloat, RoundUp) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.100000000000000000000000000000000000000000000000000000000000000000000000000003

julia> setrounding(BigFloat, RoundDown) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> setprecision(40) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.1000000000004
```

!!! warning
    La relación entre [`setprecision`](@ref) o [`setrounding`](@ref) y [`@big_str`](@ref), el macro utilizado para literales de cadena `big` (como `big"0.3"`), puede no ser intuitivo, como consecuencia del hecho de que `@big_str` es un macro. Consulte la documentación de `4d61726b646f776e2e436f64652822222c2022406269675f7374722229_40726566` para más detalles.


## [Numeric Literal Coefficients](@id man-numeric-literal-coefficients)

Para hacer que las fórmulas y expresiones numéricas comunes sean más claras, Julia permite que las variables sean precedidas inmediatamente por un literal numérico, lo que implica multiplicación. Esto hace que escribir expresiones polinómicas sea mucho más limpio:

```jldoctest numeric-coefficients
julia> x = 3
3

julia> 2x^2 - 3x + 1
10

julia> 1.5x^2 - .5x + 1
13.0
```

También hace que escribir funciones exponenciales sea más elegante:

```jldoctest numeric-coefficients
julia> 2^2x
64
```

La precedencia de los coeficientes literales numéricos es ligeramente inferior a la de los operadores unarios como la negación. Así que `-2x` se analiza como `(-2) * x` y `√2x` se analiza como `(√2) * x`. Sin embargo, los coeficientes literales numéricos se analizan de manera similar a los operadores unarios cuando se combinan con la exponenciación. Por ejemplo, `2^3x` se analiza como `2^(3x)`, y `2x^3` se analiza como `2*(x^3)`.

Los literales numéricos también funcionan como coeficientes de expresiones entre paréntesis:

```jldoctest numeric-coefficients
julia> 2(x-1)^2 - 3(x-1) + 1
3
```

!!! note
    La precedencia de los coeficientes literales numéricos utilizados para la multiplicación implícita es mayor que la de otros operadores binarios como la multiplicación (`*`) y la división (`/`, `\` y `//`). Esto significa, por ejemplo, que `1 / 2im` es igual a `-0.5im` y `6 // 2(2 + 1)` es igual a `1 // 1`.


Además, las expresiones entre paréntesis se pueden usar como coeficientes de variables, lo que implica la multiplicación de la expresión por la variable:

```jldoctest numeric-coefficients
julia> (x-1)x
6
```

Ni la yuxtaposición de dos expresiones entre paréntesis, ni colocar una variable antes de una expresión entre paréntesis, sin embargo, pueden usarse para implicar multiplicación:

```jldoctest numeric-coefficients
julia> (x-1)(x+1)
ERROR: MethodError: objects of type Int64 are not callable

julia> x(x+1)
ERROR: MethodError: objects of type Int64 are not callable
```

Ambas expresiones se interpretan como aplicación de funciones: cualquier expresión que no sea un literal numérico, cuando es seguida inmediatamente por un paréntesis, se interpreta como una función aplicada a los valores en paréntesis (ver [Functions](@ref) para más información sobre funciones). Así, en ambos casos, ocurre un error ya que el valor de la izquierda no es una función.

Las mejoras sintácticas anteriores reducen significativamente el ruido visual que se produce al escribir fórmulas matemáticas comunes. Tenga en cuenta que no puede haber espacio en blanco entre un coeficiente numérico literal y el identificador o la expresión entre paréntesis que multiplica.

### Syntax Conflicts

La sintaxis del coeficiente literal en yuxtaposición puede entrar en conflicto con algunas sintaxis de literales numéricos: literales enteros hexadecimales, octales y binarios, así como la notación de ingeniería para literales de punto flotante. Aquí hay algunas situaciones donde surgen conflictos sintácticos:

  * La expresión literal entera hexadecimal `0xff` podría interpretarse como el literal numérico `0` multiplicado por la variable `xff`. Ambigüedades similares surgen con literales octales y binarios como `0o777` o `0b01001010`.
  * La expresión literal de punto flotante `1e10` podría interpretarse como el literal numérico `1` multiplicado por la variable `e10`, y de manera similar con la forma equivalente `E`.
  * La expresión literal de punto flotante de 32 bits `1.5f22` podría interpretarse como el literal numérico `1.5` multiplicado por la variable `f22`.

En todos los casos, la ambigüedad se resuelve a favor de la interpretación como literales numéricos:

  * Las expresiones que comienzan con `0x`/`0o`/`0b` son siempre literales hexadecimales/octales/binarios.
  * Las expresiones que comienzan con un literal numérico seguido de `e` o `E` son siempre literales de punto flotante.
  * Las expresiones que comienzan con un literal numérico seguido de `f` son siempre literales de punto flotante de 32 bits.

A diferencia de `E`, que es equivalente a `e` en literales numéricos por razones históricas, `F` es solo otra letra y no se comporta como `f` en literales numéricos. Por lo tanto, las expresiones que comienzan con un literal numérico seguido de `F` se interpretan como el literal numérico multiplicado por una variable, lo que significa que, por ejemplo, `1.5F22` es igual a `1.5 * F22`.

## Literal zero and one

Julia proporciona funciones que devuelven 0 y 1 literales correspondientes a un tipo especificado o al tipo de una variable dada.

| Function          | Description                                      |
|:----------------- |:------------------------------------------------ |
| [`zero(x)`](@ref) | Literal zero of type `x` or type of variable `x` |
| [`one(x)`](@ref)  | Literal one of type `x` or type of variable `x`  |

Estas funciones son útiles en [Numeric Comparisons](@ref) para evitar la sobrecarga de [type conversion](@ref conversion-and-promotion) innecesaria.

Ejemplos:

```jldoctest
julia> zero(Float32)
0.0f0

julia> zero(1.0)
0.0

julia> one(Int32)
1

julia> one(BigFloat)
1.0
```
