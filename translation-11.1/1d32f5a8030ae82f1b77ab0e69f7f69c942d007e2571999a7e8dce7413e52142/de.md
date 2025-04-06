# Mathematical Operations and Elementary Functions

Julia bietet eine vollständige Sammlung grundlegender arithmetischer und bitweiser Operatoren für alle ihre numerischen primitiven Typen sowie tragbare, effiziente Implementierungen einer umfassenden Sammlung standardmäßiger mathematischer Funktionen.

## Arithmetic Operators

Die folgenden [arithmetic operators](https://en.wikipedia.org/wiki/Arithmetic#Arithmetic_operations) werden auf allen primitiven numerischen Typen unterstützt:

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

Ein numerischer Literal, der direkt vor einem Bezeichner oder Klammern steht, z. B. `2x` oder `2(x + y)`, wird als Multiplikation behandelt, jedoch mit höherer Priorität als andere binäre Operationen. Siehe [Numeric Literal Coefficients](@ref man-numeric-literal-coefficients) für Details.

Julia's promotion system makes arithmetic operations on mixtures of argument types "just work" naturally and automatically. See [Conversion and Promotion](@ref conversion-and-promotion) for details of the promotion system.

Das ÷-Zeichen kann bequem eingegeben werden, indem man `\div<tab>` in die REPL oder die Julia IDE schreibt. Siehe die [manual section on Unicode input](@ref Unicode-Input) für weitere Informationen.

Hier sind einige einfache Beispiele mit arithmetischen Operatoren:

```jldoctest
julia> 1 + 2 + 3
6

julia> 1 - 2
-1

julia> 3*2/12
0.5
```

(Üblicherweise neigen wir dazu, Operatoren enger zu setzen, wenn sie vor anderen nahegelegenen Operatoren angewendet werden. Zum Beispiel würden wir allgemein `-x + 2` schreiben, um zu verdeutlichen, dass zuerst `x` negiert wird und dann `2` zu diesem Ergebnis addiert wird.)

Wenn `false` in der Multiplikation verwendet wird, fungiert es als *starker Null*:

```jldoctest
julia> NaN * false
0.0

julia> false * Inf
0.0
```

Dies ist nützlich, um die Ausbreitung von `NaN`-Werten in Mengen zu verhindern, von denen bekannt ist, dass sie null sind. Siehe [Knuth (1992)](https://arxiv.org/abs/math/9205211) für die Motivation.

## Boolean Operators

Die folgenden [Boolean operators](https://en.wikipedia.org/wiki/Boolean_algebra#Operations) werden auf [`Bool`](@ref) Typen unterstützt:

| Expression | Name                                                    |
|:---------- |:------------------------------------------------------- |
| `!x`       | negation                                                |
| `x && y`   | [short-circuiting and](@ref man-conditional-evaluation) |
| `x \|\| y` | [short-circuiting or](@ref man-conditional-evaluation)  |

Die Negation ändert `true` in `false` und umgekehrt. Die Kurzschlussoperationen werden auf der verlinkten Seite erklärt.

Beachten Sie, dass `Bool` ein ganzzahliger Typ ist und alle üblichen Promotionsregeln und numerischen Operatoren ebenfalls darauf definiert sind.

## Bitwise Operators

Die folgenden [bitwise operators](https://en.wikipedia.org/wiki/Bitwise_operation#Bitwise_operators) werden für alle primitiven Ganzzahltypen unterstützt:

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

Hier sind einige Beispiele mit bitweisen Operatoren:

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

Jeder binäre arithmetische und bitweise Operator hat auch eine aktualisierende Version, die das Ergebnis der Operation wieder in ihren linken Operanden zuweist. Die aktualisierende Version des binären Operators wird gebildet, indem ein `=` unmittelbar nach dem Operator platziert wird. Zum Beispiel ist das Schreiben von `x += 3` äquivalent zu `x = x + 3`:

```jldoctest
julia> x = 1
1

julia> x += 3
4

julia> x
4
```

Die aktualisierten Versionen aller binären arithmetischen und bitweisen Operatoren sind:

```
+=  -=  *=  /=  \=  ÷=  %=  ^=  &=  |=  ⊻=  >>>=  >>=  <<=
```

!!! note
    Ein Aktualisierungsoperator bindet die Variable auf der linken Seite neu. Infolgedessen kann sich der Typ der Variable ändern.

    ```jldoctest
    julia> x = 0x01; typeof(x)
    UInt8

    julia> x *= 2 # Same as x = x * 2
    2

    julia> typeof(x)
    Int64
    ```


## [Vectorized "dot" operators](@id man-dot-operators)

Für *jede* binäre Operation wie `^` gibt es eine entsprechende "Punkt"-Operation `.^`, die *automatisch* definiert ist, um `^` elementweise auf Arrays auszuführen. Zum Beispiel ist `[1, 2, 3] ^ 3` nicht definiert, da es keine standardmäßige mathematische Bedeutung für das "Kubieren" eines (nicht-quadratischen) Arrays gibt, aber `[1, 2, 3] .^ 3` ist definiert als die Berechnung des elementweisen (oder "vektorisierten") Ergebnisses `[1^3, 2^3, 3^3]`. Ähnlich gibt es für unäre Operatoren wie `!` oder `√` einen entsprechenden `.√`, der den Operator elementweise anwendet.

```jldoctest
julia> [1, 2, 3] .^ 3
3-element Vector{Int64}:
  1
  8
 27
```

Genauer gesagt wird `a .^ b` als der ["dot" call](@ref man-vectorized) `(^).(a,b)` geparst, was eine [broadcast](@ref Broadcasting)-Operation durchführt: Es kann Arrays und Skalare kombinieren, Arrays derselben Größe (die Operation elementweise ausführen) und sogar Arrays unterschiedlicher Formen (z. B. das Kombinieren von Zeilen- und Spaltenvektoren zur Erzeugung einer Matrix). Darüber hinaus sind diese "Punktoperatoren", wie alle vektorisierte "Punktaufrufe", *fusionierend*. Wenn Sie beispielsweise `2 .* A.^2 .+ sin.(A)` (oder äquivalent `@. 2A^2 + sin(A)`, unter Verwendung des [`@.`](@ref @__dot__)-Makros) für ein Array `A` berechnen, führt es eine *einzelne* Schleife über `A` aus und berechnet `2a^2 + sin(a)` für jedes Element `a` von `A`. Insbesondere werden geschachtelte Punktaufrufe wie `f.(g.(x))` fusioniert, und "benachbarte" binäre Operatoren wie `x .+ 3 .* x.^2` sind äquivalent zu geschachtelten Punktaufrufen `(+).(x, (*).(3, (^).(x, 2)))`.

Furthermore, "dotted" updating operators like `a .+= b` (or `@. a += b`) are parsed as `a .= a .+ b`, where `.=` is a fused *in-place* assignment operation (see the [dot syntax documentation](@ref man-vectorized)).

Beachten Sie, dass die Punkt-Syntax auch für benutzerdefinierte Operatoren anwendbar ist. Wenn Sie beispielsweise `⊗(A, B) = kron(A, B)` definieren, um eine bequeme Infix-Syntax `A ⊗ B` für Kronecker-Produkte zu geben ([`kron`](@ref)), dann wird `[A, B] .⊗ [C, D]` `[A⊗C, B⊗D]` berechnen, ohne dass zusätzlicher Code erforderlich ist.

Die Kombination von Punktoperatoren mit numerischen Literalen kann mehrdeutig sein. Zum Beispiel ist nicht klar, ob `1.+x` `1. + x` oder `1 .+ x` bedeutet. Daher ist diese Syntax nicht erlaubt, und es müssen in solchen Fällen Leerzeichen um den Operator verwendet werden.

## Numeric Comparisons

Standardvergleichsoperationen sind für alle primitiven numerischen Typen definiert:

| Operator                     | Name                     |
|:---------------------------- |:------------------------ |
| [`==`](@ref)                 | equality                 |
| [`!=`](@ref), [`≠`](@ref !=) | inequality               |
| [`<`](@ref)                  | less than                |
| [`<=`](@ref), [`≤`](@ref <=) | less than or equal to    |
| [`>`](@ref)                  | greater than             |
| [`>=`](@ref), [`≥`](@ref >=) | greater than or equal to |

Hier sind einige einfache Beispiele:

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

Ganzzahlen werden auf die übliche Weise verglichen – durch den Vergleich von Bits. Gleitkommazahlen werden gemäß der [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008) verglichen:

  * Endliche Zahlen sind in der üblichen Weise geordnet.
  * Positives Null ist gleich, aber nicht größer als negatives Null.
  * `Inf` ist gleich sich selbst und größer als alles andere außer `NaN`.
  * `-Inf` ist gleich sich selbst und kleiner als alles andere außer `NaN`.
  * `NaN` ist weder gleich, noch kleiner als, noch größer als irgendetwas, einschließlich sich selbst.

Der letzte Punkt ist potenziell überraschend und daher erwähnenswert:

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

und kann Kopfschmerzen verursachen, wenn man mit [arrays](@ref man-multi-dim-arrays) arbeitet:

```jldoctest
julia> [1 NaN] == [1 NaN]
false
```

Julia bietet zusätzliche Funktionen, um Zahlen auf spezielle Werte zu testen, die in Situationen wie dem Vergleich von Hash-Schlüsseln nützlich sein können:

| Function                | Tests if                  |
|:----------------------- |:------------------------- |
| [`isequal(x, y)`](@ref) | `x` and `y` are identical |
| [`isfinite(x)`](@ref)   | `x` is a finite number    |
| [`isinf(x)`](@ref)      | `x` is infinite           |
| [`isnan(x)`](@ref)      | `x` is not a number       |

[`isequal`](@ref) betrachtet `NaN`s als gleich zueinander:

```jldoctest
julia> isequal(NaN, NaN)
true

julia> isequal([1 NaN], [1 NaN])
true

julia> isequal(NaN, NaN32)
true
```

`isequal` kann auch verwendet werden, um signierte Nullen zu unterscheiden:

```jldoctest
julia> -0.0 == 0.0
true

julia> isequal(-0.0, 0.0)
false
```

Vergleich von gemischten Typen zwischen vorzeichenbehafteten Ganzzahlen, vorzeichenlosen Ganzzahlen und Fließkommazahlen kann knifflig sein. Es wurde viel Sorgfalt darauf verwendet, sicherzustellen, dass Julia dies korrekt macht.

Für andere Typen ruft `isequal` standardmäßig [`==`](@ref) auf. Wenn Sie also die Gleichheit für Ihre eigenen Typen definieren möchten, müssen Sie nur eine `4d61726b646f776e2e436f64652822222c20223d3d2229_40726566`-Methode hinzufügen. Wenn Sie Ihre eigene Gleichheitsfunktion definieren, sollten Sie wahrscheinlich auch eine entsprechende [`hash`](@ref)-Methode definieren, um sicherzustellen, dass `isequal(x,y)` `hash(x) == hash(y)` impliziert.

### Chaining comparisons

Im Gegensatz zu den meisten Sprachen können mit der [notable exception of Python](https://en.wikipedia.org/wiki/Python_syntax_and_semantics#Comparison_operators) Vergleiche beliebig verkettet werden:

```jldoctest
julia> 1 < 2 <= 2 < 3 == 3 > 2 >= 1 == 1 < 3 != 5
true
```

Das Verketten von Vergleichen ist in numerischem Code oft sehr praktisch. Verkettete Vergleiche verwenden den `&&`-Operator für skalare Vergleiche und den [`&`](@ref)-Operator für elementweise Vergleiche, was es ihnen ermöglicht, auf Arrays zu arbeiten. Zum Beispiel gibt `0 .< A .< 1` ein boolesches Array zurück, dessen Einträge wahr sind, wenn die entsprechenden Elemente von `A` zwischen 0 und 1 liegen.

Beachten Sie das Bewertungsverhalten von verketteten Vergleichen:

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

Der mittlere Ausdruck wird nur einmal ausgewertet, anstatt zweimal, wie es der Fall wäre, wenn der Ausdruck als `v(1) < v(2) && v(2) <= v(3)` geschrieben wäre. Die Reihenfolge der Auswertungen in einem verketteten Vergleich ist jedoch undefiniert. Es wird dringend empfohlen, Ausdrücke mit Nebeneffekten (wie z.B. Drucken) in verketteten Vergleichen nicht zu verwenden. Wenn Nebeneffekte erforderlich sind, sollte der Kurzschlussoperator `&&` ausdrücklich verwendet werden (siehe [Short-Circuit Evaluation](@ref)).

### Elementary Functions

Julia bietet eine umfassende Sammlung von mathematischen Funktionen und Operatoren. Diese mathematischen Operationen sind über eine so breite Klasse von numerischen Werten definiert, wie es sinnvolle Definitionen zulassen, einschließlich Ganzzahlen, Fließkommazahlen, rationalen Zahlen und komplexen Zahlen, wo immer solche Definitionen sinnvoll sind.

Darüber hinaus können diese Funktionen (wie jede Julia-Funktion) in "vektorisierter" Weise auf Arrays und andere Sammlungen mit [dot syntax](@ref man-vectorized) `f.(A)` angewendet werden, z. B. berechnet `sin.(A)` den Sinus jedes Elements eines Arrays `A`.

## Operator Precedence and Associativity

Julia wendet die folgende Reihenfolge und Assoziativität der Operationen an, von der höchsten Priorität bis zur niedrigsten:

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

Für eine vollständige Liste der *allen* Julia-Operatoren und deren Präzedenz, siehe den oberen Teil dieser Datei: [`src/julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm). Beachte, dass einige der dort aufgeführten Operatoren im `Base`-Modul nicht definiert sind, aber möglicherweise von Standardbibliotheken, Paketen oder Benutzer-Code Definitionen erhalten.

Sie können die numerische Priorität für jeden gegebenen Operator auch über die eingebaute Funktion `Base.operator_precedence` finden, wobei höhere Zahlen Vorrang haben:

```jldoctest
julia> Base.operator_precedence(:+), Base.operator_precedence(:*), Base.operator_precedence(:.)
(11, 12, 17)

julia> Base.operator_precedence(:sin), Base.operator_precedence(:+=), Base.operator_precedence(:(=))  # (Note the necessary parens on `:(=)`)
(0, 1, 1)
```

Ein Symbol, das die Operatorassoziativität darstellt, kann auch durch den Aufruf der eingebauten Funktion `Base.operator_associativity` gefunden werden:

```jldoctest
julia> Base.operator_associativity(:-), Base.operator_associativity(:+), Base.operator_associativity(:^)
(:left, :none, :right)

julia> Base.operator_associativity(:⊗), Base.operator_associativity(:sin), Base.operator_associativity(:→)
(:left, :none, :right)
```

Beachten Sie, dass Symbole wie `:sin` die Präzedenz `0` zurückgeben. Dieser Wert repräsentiert ungültige Operatoren und nicht Operatoren mit der niedrigsten Präzedenz. Ebenso wird solchen Operatoren die Assoziativität `:none` zugewiesen.

[Numeric literal coefficients](@ref man-numeric-literal-coefficients), z.B. `2x`, werden als Multiplikationen mit höherer Priorität als jede andere binäre Operation behandelt, mit der Ausnahme von `^`, wo sie nur als Exponent eine höhere Priorität haben.

```jldoctest
julia> x = 3; 2x^2
18

julia> x = 3; 2^2x
64
```

Die Juxtaposition wird wie ein unärer Operator geparst, der die gleiche natürliche Asymmetrie um Exponenten hat: `-x^y` und `2x^y` werden als `-(x^y)` und `2(x^y)` geparst, während `x^-y` und `x^2y` als `x^(-y)` und `x^(2y)` geparst werden.

## Numerical Conversions

Julia unterstützt drei Formen der numerischen Konvertierung, die sich in ihrer Handhabung von ungenauen Konvertierungen unterscheiden.

  * Die Notation `T(x)` oder `convert(T, x)` konvertiert `x` in einen Wert des Typs `T`.

      * Wenn `T` ein Fließkommatyp ist, ist das Ergebnis der nächstgelegene darstellbare Wert, der positiv oder negativ unendlich sein kann.
      * Wenn `T` ein Ganzzahltyp ist, wird ein `InexactError` ausgelöst, wenn `x` nicht durch `T` darstellbar ist.
  * `x % T` konvertiert eine Ganzzahl `x` in einen Wert des Ganzzahltyps `T`, der kongruent zu `x` modulo `2^n` ist, wobei `n` die Anzahl der Bits in `T` ist. Mit anderen Worten, die binäre Darstellung wird abgeschnitten, um zu passen.
  * Die [Rounding functions](@ref) nimmt einen Typ `T` als optionales Argument. Zum Beispiel ist `round(Int,x)` eine Abkürzung für `Int(round(x))`.

Die folgenden Beispiele zeigen die verschiedenen Formen.

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

Siehe [Conversion and Promotion](@ref conversion-and-promotion) für Informationen, wie du deine eigenen Konversionen und Promotionen definieren kannst.

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

Für einen Überblick darüber, warum Funktionen wie [`hypot`](@ref), [`expm1`](@ref) und [`log1p`](@ref) notwendig und nützlich sind, siehe John D. Cooks ausgezeichnete Blogbeiträge zu diesem Thema: [expm1, log1p, erfc](https://www.johndcook.com/blog/2010/06/07/math-library-functions-that-seem-unnecessary/) und [hypot](https://www.johndcook.com/blog/2010/06/02/whats-so-hard-about-finding-a-hypotenuse/).

### Trigonometric and hyperbolic functions

Alle standardmäßigen trigonometrischen und hyperbolischen Funktionen sind ebenfalls definiert:

```
sin    cos    tan    cot    sec    csc
sinh   cosh   tanh   coth   sech   csch
asin   acos   atan   acot   asec   acsc
asinh  acosh  atanh  acoth  asech  acsch
sinc   cosc
```

Dies sind alles Funktionen mit einem einzelnen Argument, wobei [`atan`](@ref) auch zwei Argumente akzeptiert, die einem traditionellen [`atan2`](https://en.wikipedia.org/wiki/Atan2) Funktion entsprechen.

Zusätzlich sind [`sinpi(x)`](@ref) und [`cospi(x)`](@ref) für genauere Berechnungen von [`sin(pi * x)`](@ref) und [`cos(pi * x)`](@ref) bereitgestellt.

Um trigonometrische Funktionen mit Grad anstelle von Bogenmaß zu berechnen, fügen Sie der Funktion ein `d` hinzu. Zum Beispiel berechnet [`sind(x)`](@ref) den Sinus von `x`, wobei `x` in Grad angegeben ist. Die vollständige Liste der trigonometrischen Funktionen mit Gradvarianten ist:

```
sind   cosd   tand   cotd   secd   cscd
asind  acosd  atand  acotd  asecd  acscd
```

### Special functions

Viele andere spezielle mathematische Funktionen werden von dem Paket [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl) bereitgestellt.
