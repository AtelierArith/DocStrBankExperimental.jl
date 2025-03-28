# Mathematical Operations and Elementary Functions

Julia proporciona una colección completa de operadores aritméticos básicos y bit a bit en todos sus tipos primitivos numéricos, así como implementaciones portátiles y eficientes de una colección integral de funciones matemáticas estándar.

## Arithmetic Operators

Los siguientes [arithmetic operators](https://en.wikipedia.org/wiki/Arithmetic#Arithmetic_operations) son compatibles con todos los tipos numéricos primitivos:

| Expression | Name           | Description                            |
|:---------- |:-------------- |:-------------------------------------- |
| `+x`       | unary plus     | the identity operation                 |
| `-x`       | unary minus    | maps values to their additive inverses |
| `x + y`    | binary plus    | performs addition                      |
| `x - y`    | binary minus   | performs subtraction                   |
| `x * y`    | times          | performs multiplication                |
| `x / y`    | divide         | performs division                      |
| `x ÷ y`    | integer divide | x / y, truncated to an integer         |
| `x \ y`    | inverse divide | equivalent to `y / x`                  |
| `x ^ y`    | power          | raises `x` to the `y`th power          |
| `x % y`    | remainder      | equivalent to `rem(x, y)`              |

Un literal numérico colocado directamente antes de un identificador o paréntesis, por ejemplo, `2x` o `2(x + y)`, se trata como una multiplicación, excepto con una precedencia más alta que otras operaciones binarias. Consulta [Numeric Literal Coefficients](@ref man-numeric-literal-coefficients) para más detalles.

Julia's promotion system makes arithmetic operations on mixtures of argument types "just work" naturally and automatically. See [Conversion and Promotion](@ref conversion-and-promotion) for details of the promotion system.

El signo ÷ se puede escribir cómodamente escribiendo `\div<tab>` en el REPL o en el IDE de Julia. Consulta el [manual section on Unicode input](@ref Unicode-Input) para más información.

Aquí hay algunos ejemplos simples utilizando operadores aritméticos:

```jldoctest
julia> 1 + 2 + 3
6

julia> 1 - 2
-1

julia> 3*2/12
0.5
```

(Por convención, tendemos a espaciar los operadores más estrechamente si se aplican antes que otros operadores cercanos. Por ejemplo, generalmente escribiríamos `-x + 2` para reflejar que primero se niega `x`, y luego se suma `2` a ese resultado.)

Cuando se utiliza en multiplicación, `false` actúa como un *cero fuerte*:

```jldoctest
julia> NaN * false
0.0

julia> false * Inf
0.0
```

Esto es útil para prevenir la propagación de valores `NaN` en cantidades que se sabe que son cero. Consulta [Knuth (1992)](https://arxiv.org/abs/math/9205211) para más información.

## Boolean Operators

Los siguientes [Boolean operators](https://en.wikipedia.org/wiki/Boolean_algebra#Operations) son compatibles con [`Bool`](@ref) tipos:

| Expression | Name                                                    |
|:---------- |:------------------------------------------------------- |
| `!x`       | negation                                                |
| `x && y`   | [short-circuiting and](@ref man-conditional-evaluation) |
| `x \|\| y` | [short-circuiting or](@ref man-conditional-evaluation)  |

La negación cambia `true` a `false` y viceversa. Las operaciones de cortocircuito se explican en la página vinculada.

Tenga en cuenta que `Bool` es un tipo de entero y todas las reglas de promoción habituales y los operadores numéricos también están definidos en él.

## Bitwise Operators

Los siguientes [bitwise operators](https://en.wikipedia.org/wiki/Bitwise_operation#Bitwise_operators) son compatibles con todos los tipos de enteros primitivos:

| Expression | Name                                                                     |
|:---------- |:------------------------------------------------------------------------ |
| `~x`       | bitwise not                                                              |
| `x & y`    | bitwise and                                                              |
| `x \| y`   | bitwise or                                                               |
| `x ⊻ y`    | bitwise xor (exclusive or)                                               |
| `x ⊼ y`    | bitwise nand (not and)                                                   |
| `x ⊽ y`    | bitwise nor (not or)                                                     |
| `x >>> y`  | [logical shift](https://en.wikipedia.org/wiki/Logical_shift) right       |
| `x >> y`   | [arithmetic shift](https://en.wikipedia.org/wiki/Arithmetic_shift) right |
| `x << y`   | logical/arithmetic shift left                                            |

Aquí hay algunos ejemplos con operadores a nivel de bits:

```jldoctest
julia> ~123
-124

julia> 123 & 234
106

julia> 123 | 234
251

julia> 123 ⊻ 234
145

julia> xor(123, 234)
145

julia> nand(123, 123)
-124

julia> 123 ⊼ 123
-124

julia> nor(123, 124)
-128

julia> 123 ⊽ 124
-128

julia> ~UInt32(123)
0xffffff84

julia> ~UInt8(123)
0x84
```

## Updating operators

Cada operador aritmético binario y operador a nivel de bits también tiene una versión de actualización que asigna el resultado de la operación de nuevo a su operando izquierdo. La versión de actualización del operador binario se forma colocando un `=` inmediatamente después del operador. Por ejemplo, escribir `x += 3` es equivalente a escribir `x = x + 3`:

```jldoctest
julia> x = 1
1

julia> x += 3
4

julia> x
4
```

Las versiones actualizadas de todos los operadores aritméticos binarios y bit a bit son:

```
+=  -=  *=  /=  \=  ÷=  %=  ^=  &=  |=  ⊻=  >>>=  >>=  <<=
```

!!! note
    Un operador de actualización vuelve a enlazar la variable en el lado izquierdo. Como resultado, el tipo de la variable puede cambiar.

    ```jldoctest
    julia> x = 0x01; typeof(x)
    UInt8

    julia> x *= 2 # Same as x = x * 2
    2

    julia> typeof(x)
    Int64
    ```


## [Vectorized "dot" operators](@id man-dot-operators)

Para *cada* operación binaria como `^`, hay una operación "punto" correspondiente `.^` que se *define automáticamente* para realizar `^` elemento por elemento en arreglos. Por ejemplo, `[1, 2, 3] ^ 3` no está definido, ya que no hay un significado matemático estándar para "elevar al cubo" un arreglo (no cuadrado), pero `[1, 2, 3] .^ 3` se define como el cálculo del resultado elemento a elemento (o "vectorizado") `[1^3, 2^3, 3^3]`. De manera similar, para operadores unarios como `!` o `√`, hay un correspondiente `.√` que aplica el operador elemento por elemento.

```jldoctest
julia> [1, 2, 3] .^ 3
3-element Vector{Int64}:
  1
  8
 27
```

Más específicamente, `a .^ b` se analiza como el ["dot" call](@ref man-vectorized) `(^).(a,b)`, que realiza una operación de [broadcast](@ref Broadcasting): puede combinar arreglos y escalares, arreglos del mismo tamaño (realizando la operación elemento a elemento), e incluso arreglos de diferentes formas (por ejemplo, combinando vectores fila y columna para producir una matriz). Además, como todas las "llamadas de punto" vectorizadas, estos "operadores de punto" son *fusionados*. Por ejemplo, si calculas `2 .* A.^2 .+ sin.(A)` (o de manera equivalente `@. 2A^2 + sin(A)`, usando el [`@.`](@ref @__dot__) macro) para un arreglo `A`, realiza un *único* bucle sobre `A`, computando `2a^2 + sin(a)` para cada elemento `a` de `A`. En particular, las llamadas de punto anidadas como `f.(g.(x))` se fusionan, y los operadores binarios "adyacentes" como `x .+ 3 .* x.^2` son equivalentes a llamadas de punto anidadas `(+).(x, (*).(3, (^).(x, 2)))`.

Furthermore, "dotted" updating operators like `a .+= b` (or `@. a += b`) are parsed as `a .= a .+ b`, where `.=` is a fused *in-place* assignment operation (see the [dot syntax documentation](@ref man-vectorized)).

Tenga en cuenta que la sintaxis de punto también es aplicable a los operadores definidos por el usuario. Por ejemplo, si define `⊗(A, B) = kron(A, B)` para dar una sintaxis infija conveniente `A ⊗ B` para productos de Kronecker ([`kron`](@ref)), entonces `[A, B] .⊗ [C, D]` calculará `[A⊗C, B⊗D]` sin codificación adicional.

Combinar operadores de punto con literales numéricos puede ser ambiguo. Por ejemplo, no está claro si `1.+x` significa `1. + x` o `1 .+ x`. Por lo tanto, esta sintaxis no está permitida, y se deben usar espacios alrededor del operador en tales casos.

## Numeric Comparisons

Las operaciones de comparación estándar están definidas para todos los tipos numéricos primitivos:

| Operator                     | Name                     |
|:---------------------------- |:------------------------ |
| [`==`](@ref)                 | equality                 |
| [`!=`](@ref), [`≠`](@ref !=) | inequality               |
| [`<`](@ref)                  | less than                |
| [`<=`](@ref), [`≤`](@ref <=) | less than or equal to    |
| [`>`](@ref)                  | greater than             |
| [`>=`](@ref), [`≥`](@ref >=) | greater than or equal to |

Aquí hay algunos ejemplos simples:

```jldoctest
julia> 1 == 1
true

julia> 1 == 2
false

julia> 1 != 2
true

julia> 1 == 1.0
true

julia> 1 < 2
true

julia> 1.0 > 3
false

julia> 1 >= 1.0
true

julia> -1 <= 1
true

julia> -1 <= -1
true

julia> -1 <= -2
false

julia> 3 < -0.5
false
```

Los enteros se comparan de la manera estándar, mediante la comparación de bits. Los números de punto flotante se comparan de acuerdo con el [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008):

  * Los números finitos están ordenados de la manera habitual.
  * Cero positivo es igual pero no mayor que cero negativo.
  * `Inf` es igual a sí mismo y mayor que todo lo demás excepto `NaN`.
  * `-Inf` es igual a sí mismo y menor que todo lo demás excepto `NaN`.
  * `NaN` no es igual a, no es menor que, y no es mayor que nada, incluyendo a sí mismo.

El último punto es potencialmente sorprendente y, por lo tanto, vale la pena señalarlo:

```jldoctest
julia> NaN == NaN
false

julia> NaN != NaN
true

julia> NaN < NaN
false

julia> NaN > NaN
false
```

y puede causar dolores de cabeza al trabajar con [arrays](@ref man-multi-dim-arrays):

```jldoctest
julia> [1 NaN] == [1 NaN]
false
```

Julia proporciona funciones adicionales para probar números en busca de valores especiales, lo que puede ser útil en situaciones como comparaciones de claves hash:

| Function                | Tests if                  |
|:----------------------- |:------------------------- |
| [`isequal(x, y)`](@ref) | `x` and `y` are identical |
| [`isfinite(x)`](@ref)   | `x` is a finite number    |
| [`isinf(x)`](@ref)      | `x` is infinite           |
| [`isnan(x)`](@ref)      | `x` is not a number       |

[`isequal`](@ref) considera que los `NaN`s son iguales entre sí:

```jldoctest
julia> isequal(NaN, NaN)
true

julia> isequal([1 NaN], [1 NaN])
true

julia> isequal(NaN, NaN32)
true
```

`isequal` también se puede utilizar para distinguir ceros con signo:

```jldoctest
julia> -0.0 == 0.0
true

julia> isequal(-0.0, 0.0)
false
```

Las comparaciones de tipos mixtos entre enteros con signo, enteros sin signo y flotantes pueden ser complicadas. Se ha tenido mucho cuidado para asegurar que Julia las realice correctamente.

Para otros tipos, `isequal` por defecto llama a [`==`](@ref), así que si deseas definir la igualdad para tus propios tipos, solo necesitas agregar un método `4d61726b646f776e2e436f64652822222c20223d3d2229_40726566`. Si defines tu propia función de igualdad, probablemente deberías definir un método correspondiente [`hash`](@ref) para asegurar que `isequal(x,y)` implica `hash(x) == hash(y)`.

### Chaining comparisons

A diferencia de la mayoría de los lenguajes, con el [notable exception of Python](https://en.wikipedia.org/wiki/Python_syntax_and_semantics#Comparison_operators), las comparaciones se pueden encadenar arbitrariamente:

```jldoctest
julia> 1 < 2 <= 2 < 3 == 3 > 2 >= 1 == 1 < 3 != 5
true
```

La comparación encadenada es a menudo bastante conveniente en el código numérico. Las comparaciones encadenadas utilizan el operador `&&` para comparaciones escalares, y el operador [`&`](@ref) para comparaciones elemento a elemento, lo que les permite funcionar en arreglos. Por ejemplo, `0 .< A .< 1` da un arreglo booleano cuyas entradas son verdaderas donde los elementos correspondientes de `A` están entre 0 y 1.

Nota el comportamiento de evaluación de las comparaciones encadenadas:

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> v(1) < v(2) <= v(3)
2
1
3
true

julia> v(1) > v(2) <= v(3)
2
1
false
```

La expresión del medio solo se evalúa una vez, en lugar de dos veces como lo haría si la expresión se escribiera como `v(1) < v(2) && v(2) <= v(3)`. Sin embargo, el orden de las evaluaciones en una comparación encadenada no está definido. Se recomienda encarecidamente no usar expresiones con efectos secundarios (como imprimir) en comparaciones encadenadas. Si se requieren efectos secundarios, se debe usar explícitamente el operador de cortocircuito `&&` (ver [Short-Circuit Evaluation](@ref)).

### Elementary Functions

Julia proporciona una colección completa de funciones y operadores matemáticos. Estas operaciones matemáticas están definidas sobre una clase tan amplia de valores numéricos como permitan definiciones sensatas, incluidos enteros, números de punto flotante, racionales y números complejos, donde tales definiciones tengan sentido.

Además, estas funciones (como cualquier función de Julia) se pueden aplicar de manera "vectorizada" a arreglos y otras colecciones con el [dot syntax](@ref man-vectorized) `f.(A)`, por ejemplo, `sin.(A)` calculará el seno de cada elemento de un arreglo `A`.

## Operator Precedence and Associativity

Julia aplica el siguiente orden y asociatividad de las operaciones, de mayor a menor precedencia:

| Category       | Operators                                              | Associativity   |
|:-------------- |:------------------------------------------------------ |:--------------- |
| Syntax         | `.` followed by `::`                                   | Left            |
| Exponentiation | `^`                                                    | Right           |
| Unary          | `+ - ! ~ ¬ √ ∛ ∜ ⋆ ± ∓ <: >:`                          | Right[^1]       |
| Bitshifts      | `<< >> >>>`                                            | Left            |
| Fractions      | `//`                                                   | Left            |
| Multiplication | `* / % & \ ÷`                                          | Left[^2]        |
| Addition       | `+ - \| ⊻`                                             | Left[^2]        |
| Syntax         | `: ..`                                                 | Left            |
| Syntax         | `\|>`                                                  | Left            |
| Syntax         | `<\|`                                                  | Right           |
| Comparisons    | `> < >= <= == === != !== <:`                           | Non-associative |
| Control flow   | `&&` followed by `\|\|` followed by `?`                | Right           |
| Pair           | `=>`                                                   | Right           |
| Assignments    | `= += -= *= /= //= \= ^= ÷= %= \|= &= ⊻= <<= >>= >>>=` | Right           |

[^1]: The unary operators `+` and `-` require explicit parentheses around their argument to disambiguate them from the operator `++`, etc. Other compositions of unary operators are parsed with right-associativity, e. g., `√√-a` as `√(√(-a))`.

[^2]: The operators `+`, `++` and `*` are non-associative. `a + b + c` is parsed as `+(a, b, c)` not `+(+(a, b), c)`. However, the fallback methods for `+(a, b, c, d...)` and `*(a, b, c, d...)` both default to left-associative evaluation.

Para una lista completa de la precedencia de *cada* operador de Julia, consulta la parte superior de este archivo: [`src/julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm). Ten en cuenta que algunos de los operadores allí no están definidos en el módulo `Base`, pero pueden tener definiciones proporcionadas por bibliotecas estándar, paquetes o código de usuario.

También puedes encontrar la precedencia numérica para cualquier operador dado a través de la función incorporada `Base.operator_precedence`, donde los números más altos tienen precedencia:

```jldoctest
julia> Base.operator_precedence(:+), Base.operator_precedence(:*), Base.operator_precedence(:.)
(11, 12, 17)

julia> Base.operator_precedence(:sin), Base.operator_precedence(:+=), Base.operator_precedence(:(=))  # (Note the necessary parens on `:(=)`)
(0, 1, 1)
```

Un símbolo que representa la asociatividad del operador también se puede encontrar llamando a la función incorporada `Base.operator_associativity`:

```jldoctest
julia> Base.operator_associativity(:-), Base.operator_associativity(:+), Base.operator_associativity(:^)
(:left, :none, :right)

julia> Base.operator_associativity(:⊗), Base.operator_associativity(:sin), Base.operator_associativity(:→)
(:left, :none, :right)
```

Tenga en cuenta que símbolos como `:sin` devuelven una precedencia de `0`. Este valor representa operadores inválidos y no operadores de menor precedencia. De manera similar, a dichos operadores se les asigna una asociatividad `:none`.

[Numeric literal coefficients](@ref man-numeric-literal-coefficients), p. ej. `2x`, se tratan como multiplicaciones con mayor precedencia que cualquier otra operación binaria, con la excepción de `^` donde tienen mayor precedencia solo como el exponente.

```jldoctest
julia> x = 3; 2x^2
18

julia> x = 3; 2^2x
64
```

La yuxtaposición se analiza como un operador unario, que tiene la misma asimetría natural alrededor de los exponentes: `-x^y` y `2x^y` se analizan como `-(x^y)` y `2(x^y)`, mientras que `x^-y` y `x^2y` se analizan como `x^(-y)` y `x^(2y)`.

## Numerical Conversions

Julia admite tres formas de conversión numérica, que difieren en su manejo de conversiones inexactas.

  * La notación `T(x)` o `convert(T, x)` convierte `x` en un valor del tipo `T`.

      * Si `T` es un tipo de punto flotante, el resultado es el valor representable más cercano, que podría ser infinito positivo o negativo.
      * Si `T` es un tipo entero, se genera un `InexactError` si `x` no es representable por `T`.
  * `x % T` convierte un entero `x` a un valor del tipo entero `T` congruente con `x` módulo `2^n`, donde `n` es el número de bits en `T`. En otras palabras, la representación binaria se trunca para ajustarse.
  * El [Rounding functions](@ref) toma un tipo `T` como un argumento opcional. Por ejemplo, `round(Int,x)` es una forma abreviada de `Int(round(x))`.

Los siguientes ejemplos muestran las diferentes formas.

```jldoctest
julia> Int8(127)
127

julia> Int8(128)
ERROR: InexactError: trunc(Int8, 128)
Stacktrace:
[...]

julia> Int8(127.0)
127

julia> Int8(3.14)
ERROR: InexactError: Int8(3.14)
Stacktrace:
[...]

julia> Int8(128.0)
ERROR: InexactError: Int8(128.0)
Stacktrace:
[...]

julia> 127 % Int8
127

julia> 128 % Int8
-128

julia> round(Int8,127.4)
127

julia> round(Int8,127.6)
ERROR: InexactError: Int8(128.0)
Stacktrace:
[...]
```

Vea [Conversion and Promotion](@ref conversion-and-promotion) para saber cómo definir sus propias conversiones y promociones.

### Rounding functions

| Function              | Description                      | Return type |
|:--------------------- |:-------------------------------- |:----------- |
| [`round(x)`](@ref)    | round `x` to the nearest integer | `typeof(x)` |
| [`round(T, x)`](@ref) | round `x` to the nearest integer | `T`         |
| [`floor(x)`](@ref)    | round `x` towards `-Inf`         | `typeof(x)` |
| [`floor(T, x)`](@ref) | round `x` towards `-Inf`         | `T`         |
| [`ceil(x)`](@ref)     | round `x` towards `+Inf`         | `typeof(x)` |
| [`ceil(T, x)`](@ref)  | round `x` towards `+Inf`         | `T`         |
| [`trunc(x)`](@ref)    | round `x` towards zero           | `typeof(x)` |
| [`trunc(T, x)`](@ref) | round `x` towards zero           | `T`         |

### Division functions

| Function                   | Description                                                                                               |
|:-------------------------- |:--------------------------------------------------------------------------------------------------------- |
| [`div(x, y)`](@ref), `x÷y` | truncated division; quotient rounded towards zero                                                         |
| [`fld(x, y)`](@ref)        | floored division; quotient rounded towards `-Inf`                                                         |
| [`cld(x, y)`](@ref)        | ceiling division; quotient rounded towards `+Inf`                                                         |
| [`rem(x, y)`](@ref), `x%y` | remainder; satisfies `x == div(x, y)*y + rem(x, y)`; sign matches `x`                                     |
| [`mod(x, y)`](@ref)        | modulus; satisfies `x == fld(x, y)*y + mod(x, y)`; sign matches `y`                                       |
| [`mod1(x, y)`](@ref)       | `mod` with offset 1; returns `r∈(0, y]` for `y>0` or `r∈[y, 0)` for `y<0`, where `mod(r, y) == mod(x, y)` |
| [`mod2pi(x)`](@ref)        | modulus with respect to 2pi;  `0 <= mod2pi(x) < 2pi`                                                      |
| [`divrem(x, y)`](@ref)     | returns `(div(x, y),rem(x, y))`                                                                           |
| [`fldmod(x, y)`](@ref)     | returns `(fld(x, y), mod(x, y))`                                                                          |
| [`gcd(x, y...)`](@ref)     | greatest positive common divisor of `x`, `y`,...                                                          |
| [`lcm(x, y...)`](@ref)     | least positive common multiple of `x`, `y`,...                                                            |

### Sign and absolute value functions

| Function                 | Description                                                |
|:------------------------ |:---------------------------------------------------------- |
| [`abs(x)`](@ref)         | a positive value with the magnitude of `x`                 |
| [`abs2(x)`](@ref)        | the squared magnitude of `x`                               |
| [`sign(x)`](@ref)        | indicates the sign of `x`, returning -1, 0, or +1          |
| [`signbit(x)`](@ref)     | indicates whether the sign bit is on (true) or off (false) |
| [`copysign(x, y)`](@ref) | a value with the magnitude of `x` and the sign of `y`      |
| [`flipsign(x, y)`](@ref) | a value with the magnitude of `x` and the sign of `x*y`    |

### Powers, logs and roots

| Function                 | Description                                                                |
|:------------------------ |:-------------------------------------------------------------------------- |
| [`sqrt(x)`](@ref), `√x`  | square root of `x`                                                         |
| [`cbrt(x)`](@ref), `∛x`  | cube root of `x`                                                           |
| [`hypot(x, y)`](@ref)    | hypotenuse of right-angled triangle with other sides of length `x` and `y` |
| [`exp(x)`](@ref)         | natural exponential function at `x`                                        |
| [`expm1(x)`](@ref)       | accurate `exp(x) - 1` for `x` near zero                                    |
| [`ldexp(x, n)`](@ref)    | `x * 2^n` computed efficiently for integer values of `n`                   |
| [`log(x)`](@ref)         | natural logarithm of `x`                                                   |
| [`log(b, x)`](@ref)      | base `b` logarithm of `x`                                                  |
| [`log2(x)`](@ref)        | base 2 logarithm of `x`                                                    |
| [`log10(x)`](@ref)       | base 10 logarithm of `x`                                                   |
| [`log1p(x)`](@ref)       | accurate `log(1 + x)` for `x` near zero                                    |
| [`exponent(x)`](@ref)    | binary exponent of `x`                                                     |
| [`significand(x)`](@ref) | binary significand (a.k.a. mantissa) of a floating-point number `x`        |

Para una visión general de por qué funciones como [`hypot`](@ref), [`expm1`](@ref), y [`log1p`](@ref) son necesarias y útiles, consulte la excelente pareja de publicaciones de blog de John D. Cook sobre el tema: [expm1, log1p, erfc](https://www.johndcook.com/blog/2010/06/07/math-library-functions-that-seem-unnecessary/), y [hypot](https://www.johndcook.com/blog/2010/06/02/whats-so-hard-about-finding-a-hypotenuse/).

### Trigonometric and hyperbolic functions

Todas las funciones trigonométricas e hiperbólicas estándar también están definidas:

```
sin    cos    tan    cot    sec    csc
sinh   cosh   tanh   coth   sech   csch
asin   acos   atan   acot   asec   acsc
asinh  acosh  atanh  acoth  asech  acsch
sinc   cosc
```

Estos son todos funciones de un solo argumento, con [`atan`](@ref) también aceptando dos argumentos que corresponden a una función tradicional [`atan2`](https://en.wikipedia.org/wiki/Atan2).

Además, [`sinpi(x)`](@ref) y [`cospi(x)`](@ref) se proporcionan para cálculos más precisos de [`sin(pi * x)`](@ref) y [`cos(pi * x)`](@ref) respectivamente.

Para calcular funciones trigonométricas con grados en lugar de radianes, añade el sufijo `d` a la función. Por ejemplo, [`sind(x)`](@ref) calcula el seno de `x` donde `x` se especifica en grados. La lista completa de funciones trigonométricas con variantes en grados es:

```
sind   cosd   tand   cotd   secd   cscd
asind  acosd  atand  acotd  asecd  acscd
```

### Special functions

Muchas otras funciones matemáticas especiales son proporcionadas por el paquete [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl).
