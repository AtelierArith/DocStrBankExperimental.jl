# Integers and Floating-Point Numbers

Ganzzahlen und Fließkommawerte sind die grundlegenden Bausteine der Arithmetik und Berechnung. Eingebaute Darstellungen solcher Werte werden als numerische Primitiven bezeichnet, während Darstellungen von Ganzzahlen und Fließkommazahlen als unmittelbare Werte im Code als numerische Literale bekannt sind. Zum Beispiel ist `1` ein ganzzahliges Literal, während `1.0` ein Fließkomma-Literal ist; ihre binären In-Memory-Darstellungen als Objekte sind numerische Primitiven.

Julia bietet eine breite Palette von primitiven numerischen Typen, und eine vollständige Ergänzung von arithmetischen und bitweisen Operatoren sowie standardmäßigen mathematischen Funktionen sind über sie definiert. Diese entsprechen direkt den numerischen Typen und Operationen, die nativ auf modernen Computern unterstützt werden, wodurch Julia die Rechenressourcen voll ausnutzen kann. Darüber hinaus bietet Julia Softwareunterstützung für [Arbitrary Precision Arithmetic](@ref), die Operationen auf numerischen Werten durchführen kann, die in nativen Hardware-Darstellungen nicht effektiv dargestellt werden können, jedoch auf Kosten einer relativ langsameren Leistung.

Die folgenden sind Julias primitive numerische Typen:

  * **Ganzzahltypen:**

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

  * **Gleitkommatypen:**

| Type              | Precision                                                                      | Number of bits |
|:----------------- |:------------------------------------------------------------------------------ |:-------------- |
| [`Float16`](@ref) | [half](https://en.wikipedia.org/wiki/Half-precision_floating-point_format)     | 16             |
| [`Float32`](@ref) | [single](https://en.wikipedia.org/wiki/Single_precision_floating-point_format) | 32             |
| [`Float64`](@ref) | [double](https://en.wikipedia.org/wiki/Double_precision_floating-point_format) | 64             |

Zusätzlich wird die vollständige Unterstützung für [Complex and Rational Numbers](@ref) auf diesen primitiven numerischen Typen aufgebaut. Alle numerischen Typen interagieren natürlich ohne explizites Casting, dank einer flexiblen, benutzererweiterbaren [type promotion system](@ref conversion-and-promotion).

## Integers

Literale Ganzzahlen werden auf die standardmäßige Weise dargestellt:

```jldoctest
julia> 1
1

julia> 1234
1234
```

Der Standardtyp für ein ganzzahliges Literal hängt davon ab, ob das Zielsystem eine 32-Bit-Architektur oder eine 64-Bit-Architektur hat:

```julia-repl
# 32-bit system:
julia> typeof(1)
Int32

# 64-bit system:
julia> typeof(1)
Int64
```

Die interne Julia-Variable [`Sys.WORD_SIZE`](@ref) zeigt an, ob das Zielsystem 32-Bit oder 64-Bit ist:

```julia-repl
# 32-bit system:
julia> Sys.WORD_SIZE
32

# 64-bit system:
julia> Sys.WORD_SIZE
64
```

Julia definiert auch die Typen `Int` und `UInt`, die Aliase für die signierten und unsignierten nativen Ganzzahltypen des Systems sind:

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

Größere Ganzzahl-Literale, die nicht nur mit 32 Bit dargestellt werden können, aber in 64 Bit dargestellt werden können, erzeugen immer 64-Bit-Ganzzahlen, unabhängig vom Systemtyp:

```jldoctest
# 32-bit or 64-bit system:
julia> typeof(3000000000)
Int64
```

Vorzeichenlose Ganzzahlen werden mit dem Präfix `0x` und den hexadezimalen (Basis 16) Ziffern `0-9a-f` (die großgeschriebenen Ziffern `A-F` funktionieren ebenfalls für die Eingabe) eingegeben und ausgegeben. Die Größe des vorzeichenlosen Wertes wird durch die Anzahl der verwendeten Hexadezimalziffern bestimmt:

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

Dieses Verhalten basiert auf der Beobachtung, dass man bei der Verwendung von unsigned Hexadezimalliteralen für Ganzzahlen typischerweise versucht, eine feste numerische Bytefolge darzustellen, anstatt nur einen ganzzahligen Wert.

Binär- und Oktal-Literale werden ebenfalls unterstützt:

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

Was die hexadezimalen Literale betrifft, erzeugen binäre und oktale Literale nicht signierte Ganzzahltypen. Die Größe des binären Datenelements ist die minimal benötigte Größe, wenn die führende Ziffer des Literals nicht `0` ist. Im Falle von führenden Nullen wird die Größe durch die minimal benötigte Größe für ein Literal bestimmt, das die gleiche Länge hat, aber die führende Ziffer `1`. Das bedeutet, dass:

  * `0x1` und `0x12` sind `UInt8` Literale,
  * `0x123` und `0x1234` sind `UInt16` Literale,
  * `0x12345` und `0x12345678` sind `UInt32` Literale,
  * `0x123456789` und `0x1234567890adcdef` sind `UInt64` Literale, usw.

Selbst wenn es führende Nullziffern gibt, die keinen Beitrag zum Wert leisten, zählen sie zur Bestimmung der Speichergröße eines Literals. Daher ist `0x01` ein `UInt8`, während `0x0001` ein `UInt16` ist.

Das ermöglicht es dem Benutzer, die Größe zu steuern.

Unsigned Literale (beginnend mit `0x`), die Ganzzahlen kodieren, die zu groß sind, um als `UInt128`-Werte dargestellt zu werden, erzeugen stattdessen `BigInt`-Werte. Dies ist kein unsigned Typ, aber es ist der einzige eingebaute Typ, der groß genug ist, um solche großen Ganzzahlen darzustellen.

Binär-, oktal- und hexadezimale Literale können durch ein `-` unmittelbar vor dem unsigned Literal signiert werden. Sie erzeugen eine unsigned Ganzzahl der gleichen Größe wie das unsigned Literal, wobei das Zweierkomplement des Wertes verwendet wird:

```jldoctest
julia> -0x2
0xfe

julia> -0x0002
0xfffe
```

Die minimalen und maximalen darstellbaren Werte primitiver numerischer Typen wie Ganzzahlen werden durch die [`typemin`](@ref) und [`typemax`](@ref) Funktionen angegeben:

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

Die von [`typemin`](@ref) und [`typemax`](@ref) zurückgegebenen Werte sind immer vom angegebenen Argumenttyp. (Der obige Ausdruck verwendet mehrere Funktionen, die noch nicht eingeführt wurden, einschließlich [for loops](@ref man-loops), [Strings](@ref man-strings) und [Interpolation](@ref string-interpolation), sollte aber für Benutzer mit etwas vorhandener Programmiererfahrung leicht verständlich sein.)

### Overflow behavior

In Julia führt das Überschreiten des maximal darstellbaren Wertes eines bestimmten Typs zu einem Überlaufverhalten:

```jldoctest
julia> x = typemax(Int64)
9223372036854775807

julia> x + 1
-9223372036854775808

julia> x + 1 == typemin(Int64)
true
```

Arithmetische Operationen mit Julias Ganzzahltypen führen von Natur aus [modular arithmetic](https://en.wikipedia.org/wiki/Modular_arithmetic) aus, was die Eigenschaften der Ganzzahlarithmetik auf moderner Computerhardware widerspiegelt. In Szenarien, in denen Überlauf eine Möglichkeit darstellt, ist es entscheidend, explizit auf die Auswirkungen von Überläufen zu überprüfen, die aus solchen Überläufen resultieren können. Das [`Base.Checked`](@ref)-Modul bietet eine Reihe von arithmetischen Operationen mit Überlaufprüfungen, die Fehler auslösen, wenn ein Überlauf auftritt. Für Anwendungsfälle, in denen Überlauf unter keinen Umständen toleriert werden kann, ist es ratsam, den [`BigInt`](@ref)-Typ zu verwenden, wie in [Arbitrary Precision Arithmetic](@ref) beschrieben.

Ein Beispiel für Überlaufverhalten und wie man es potenziell lösen kann, ist wie folgt:

```jldoctest
julia> 10^19
-8446744073709551616

julia> big(10)^19
10000000000000000000
```

### Division errors

Ganzzahlige Division (die `div`-Funktion) hat zwei Ausnahmefälle: Division durch Null und Division der niedrigsten negativen Zahl ([`typemin`](@ref)) durch -1. Beide dieser Fälle werfen eine [`DivideError`](@ref). Die Rest- und Modulusfunktionen (`rem` und `mod`) werfen eine `4d61726b646f776e2e436f64652822222c20224469766964654572726f722229_40726566`, wenn ihr zweites Argument Null ist.

## Floating-Point Numbers

Literale Fließkommazahlen werden in den Standardformaten dargestellt, wobei [E-notation](https://en.wikipedia.org/wiki/Scientific_notation#E_notation) verwendet wird, wenn dies erforderlich ist:

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

Die obigen Ergebnisse sind alle [`Float64`](@ref) Werte. Literale [`Float32`](@ref) Werte können eingegeben werden, indem man ein `f` anstelle von `e` schreibt:

```jldoctest
julia> x = 0.5f0
0.5f0

julia> typeof(x)
Float32

julia> 2.5f-4
0.00025f0
```

Werte können leicht in [`Float32`](@ref) umgewandelt werden:

```jldoctest
julia> x = Float32(-1.5)
-1.5f0

julia> typeof(x)
Float32
```

Hexadezimale Fließkomma-Literale sind ebenfalls gültig, jedoch nur als [`Float64`](@ref) Werte, mit `p`, das dem Basis-2-Exponenten vorangestellt ist:

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

Halbgenaue Gleitkommazahlen werden ebenfalls unterstützt ([`Float16`](@ref)), aber sie werden softwareseitig implementiert und verwenden [`Float32`](@ref) für Berechnungen.

```jldoctest
julia> sizeof(Float16(4.))
2

julia> 2*Float16(4.)
Float16(8.0)
```

Der Unterstrich `_` kann als Zifferntrennzeichen verwendet werden:

```jldoctest
julia> 10_000, 0.000_000_005, 0xdead_beef, 0b1011_0010
(10000, 5.0e-9, 0xdeadbeef, 0xb2)
```

### Floating-point zero

Gleitkommazahlen haben [two zeros](https://en.wikipedia.org/wiki/Signed_zero), positive Null und negative Null. Sie sind gleich, haben jedoch unterschiedliche binäre Darstellungen, wie man mit der [`bitstring`](@ref) Funktion sehen kann:

```jldoctest
julia> 0.0 == -0.0
true

julia> bitstring(0.0)
"0000000000000000000000000000000000000000000000000000000000000000"

julia> bitstring(-0.0)
"1000000000000000000000000000000000000000000000000000000000000000"
```

### Special floating-point values

Es gibt drei festgelegte Standard-Gleitkommawerte, die keinem Punkt auf der reellen Zahlengeraden entsprechen:

| `Float16` | `Float32` | `Float64` | Name              | Description                                                     |
|:--------- |:--------- |:--------- |:----------------- |:--------------------------------------------------------------- |
| `Inf16`   | `Inf32`   | `Inf`     | positive infinity | a value greater than all finite floating-point values           |
| `-Inf16`  | `-Inf32`  | `-Inf`    | negative infinity | a value less than all finite floating-point values              |
| `NaN16`   | `NaN32`   | `NaN`     | not a number      | a value not `==` to any floating-point value (including itself) |

Für eine weitere Diskussion darüber, wie diese nicht-finite Gleitkommawerte in Bezug zueinander und zu anderen Gleitkommawerten angeordnet sind, siehe [Numeric Comparisons](@ref). Durch die [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008) sind diese Gleitkommawerte die Ergebnisse bestimmter arithmetischer Operationen:

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

Die [`typemin`](@ref) und [`typemax`](@ref) Funktionen gelten auch für Fließkommatypen:

```jldoctest
julia> (typemin(Float16),typemax(Float16))
(-Inf16, Inf16)

julia> (typemin(Float32),typemax(Float32))
(-Inf32, Inf32)

julia> (typemin(Float64),typemax(Float64))
(-Inf, Inf)
```

### Machine epsilon

Die meisten reellen Zahlen können nicht genau mit Fließkommazahlen dargestellt werden, und daher ist es für viele Zwecke wichtig, den Abstand zwischen zwei benachbarten darstellbaren Fließkommazahlen zu kennen, der oft als [machine epsilon](https://en.wikipedia.org/wiki/Machine_epsilon) bekannt ist.

Julia liefert [`eps`](@ref), was den Abstand zwischen `1.0` und dem nächstgrößeren darstellbaren Fließkommawert angibt:

```jldoctest
julia> eps(Float32)
1.1920929f-7

julia> eps(Float64)
2.220446049250313e-16

julia> eps() # same as eps(Float64)
2.220446049250313e-16
```

Diese Werte sind `2.0^-23` und `2.0^-52` als [`Float32`](@ref) und [`Float64`](@ref), jeweils. Die Funktion [`eps`](@ref) kann auch einen Gleitkommawert als Argument annehmen und gibt die absolute Differenz zwischen diesem Wert und dem nächsten darstellbaren Gleitkommawert zurück. Das heißt, `eps(x)` ergibt einen Wert vom gleichen Typ wie `x`, sodass `x + eps(x)` der nächste darstellbare Gleitkommawert ist, der größer als `x` ist:

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

Der Abstand zwischen zwei benachbarten darstellbaren Gleitkommazahlen ist nicht konstant, sondern kleiner für kleinere Werte und größer für größere Werte. Mit anderen Worten, die darstellbaren Gleitkommazahlen sind in der Nähe von Null am dichtesten auf der reellen Zahlengeraden und werden exponentiell spärlicher, je weiter man sich von Null entfernt. Per Definition ist `eps(1.0)` dasselbe wie `eps(Float64)`, da `1.0` ein 64-Bit-Gleitkommawert ist.

Julia bietet auch die Funktionen [`nextfloat`](@ref) und [`prevfloat`](@ref), die jeweils die nächstgrößere oder nächstkleinere darstellbare Fließkommazahl zum Argument zurückgeben:

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

Dieses Beispiel hebt das allgemeine Prinzip hervor, dass die benachbarten darstellbaren Gleitkommazahlen auch benachbarte binäre Ganzzahl-Darstellungen haben.

### Rounding modes

Wenn eine Zahl keine exakte Fließkommadarstellung hat, muss sie auf einen geeigneten darstellbaren Wert gerundet werden. Die Art und Weise, wie diese Rundung erfolgt, kann jedoch geändert werden, wenn dies gemäß den Rundungsmodi erforderlich ist, die in der [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008) präsentiert werden.

Der standardmäßig verwendete Modus ist immer [`RoundNearest`](@ref), der auf den nächstgelegenen darstellbaren Wert rundet, wobei bei Gleichständen auf den nächstgelegenen Wert mit einer geraden niedrigsten signifikanten Stelle gerundet wird.

### Background and References

Fließkommaarithmetik beinhaltet viele Feinheiten, die für Benutzer, die mit den niedrigstufigen Implementierungsdetails nicht vertraut sind, überraschend sein können. Diese Feinheiten werden jedoch in den meisten Büchern über wissenschaftliches Rechnen sowie in den folgenden Referenzen ausführlich beschrieben:

  * Der definitive Leitfaden zur Fließkommaarithmetik ist die [IEEE 754-2008 Standard](https://standards.ieee.org/standard/754-2008.html); jedoch ist er nicht kostenlos online verfügbar.
  * Für eine kurze, aber klare Präsentation darüber, wie Fließkommazahlen dargestellt werden, siehe John D. Cooks [article](https://www.johndcook.com/blog/2009/04/06/anatomy-of-a-floating-point-number/) zu diesem Thema sowie seine [introduction](https://www.johndcook.com/blog/2009/04/06/numbers-are-a-leaky-abstraction/) zu einigen der Probleme, die sich daraus ergeben, wie diese Darstellung sich im Verhalten von der idealisierten Abstraktion der reellen Zahlen unterscheidet.
  * Auch empfohlen wird Bruce Dawsons [series of blog posts on floating-point numbers](https://randomascii.wordpress.com/2012/05/20/thats-not-normalthe-performance-of-odd-floats/).
  * Für eine ausgezeichnete, umfassende Diskussion über Fließkommazahlen und Probleme der numerischen Genauigkeit, die beim Rechnen mit ihnen auftreten, siehe David Goldbergs Papier [What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.22.6768&rep=rep1&type=pdf).
  * Für noch umfangreichere Dokumentationen zur Geschichte, den Gründen und den Problemen mit Fließkommazahlen sowie zur Diskussion vieler anderer Themen der numerischen Berechnung siehe die [collected writings](https://people.eecs.berkeley.edu/~wkahan/) von [William Kahan](https://en.wikipedia.org/wiki/William_Kahan), allgemein bekannt als der "Vater der Fließkommazahlen". Besonders interessant könnte [An Interview with the Old Man of Floating-Point](https://people.eecs.berkeley.edu/~wkahan/ieee754status/754story.html) sein.

## Arbitrary Precision Arithmetic

Um Berechnungen mit Ganzzahlen und Fließkommazahlen mit beliebiger Präzision zu ermöglichen, umschließt Julia die [GNU Multiple Precision Arithmetic Library (GMP)](https://gmplib.org) und die [GNU MPFR Library](https://www.mpfr.org). Die Typen [`BigInt`](@ref) und [`BigFloat`](@ref) sind in Julia für Ganzzahlen und Fließkommazahlen mit beliebiger Präzision verfügbar.

Konstruktoren existieren, um diese Typen aus primitiven numerischen Typen zu erstellen, und die [string literal](@ref non-standard-string-literals) [`@big_str`](@ref) oder [`parse`](@ref) können verwendet werden, um sie aus `AbstractString`s zu konstruieren. `BigInt`s können auch als Ganzzahl-Literale eingegeben werden, wenn sie zu groß für andere eingebaute Ganzzahltypen sind. Beachten Sie, dass es in `Base` keinen unsigned arbiträren Präzisions-Ganzzahltyp gibt (in den meisten Fällen ist `BigInt` ausreichend), hexadezimale, oktale und binäre Literale können verwendet werden (neben dezimalen Literalen).

Sobald sie erstellt sind, nehmen sie an der Arithmetik mit allen anderen numerischen Typen teil, dank Julias [type promotion and conversion mechanism](@ref conversion-and-promotion):

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

Allerdings ist die Typumwandlung zwischen den oben genannten primitiven Typen und [`BigInt`](@ref)/[`BigFloat`](@ref) nicht automatisch und muss ausdrücklich angegeben werden.

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

Die Standardgenauigkeit (in Anzahl der Bits des Signifikanten) und der Rundungsmodus von [`BigFloat`](@ref)-Operationen können global geändert werden, indem [`setprecision`](@ref) und [`setrounding`](@ref) aufgerufen werden, und alle weiteren Berechnungen werden diese Änderungen berücksichtigen. Alternativ kann die Genauigkeit oder die Rundung nur innerhalb der Ausführung eines bestimmten Codeblocks geändert werden, indem dieselben Funktionen mit einem `do`-Block verwendet werden:

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
    Die Beziehung zwischen [`setprecision`](@ref) oder [`setrounding`](@ref) und [`@big_str`](@ref), dem Makro, das für `big`-String-Literale (wie `big"0.3"`) verwendet wird, ist möglicherweise nicht intuitiv, was eine Folge der Tatsache ist, dass `@big_str` ein Makro ist. Siehe die Dokumentation zu `4d61726b646f776e2e436f64652822222c2022406269675f7374722229_40726566` für weitere Details.


## [Numeric Literal Coefficients](@id man-numeric-literal-coefficients)

Um gängige numerische Formeln und Ausdrücke klarer zu gestalten, erlaubt Julia, dass Variablen unmittelbar von einer numerischen Konstante vorangestellt werden, was Multiplikation impliziert. Dies macht das Schreiben von polynomialen Ausdrücken viel übersichtlicher:

```jldoctest numeric-coefficients
julia> x = 3
3

julia> 2x^2 - 3x + 1
10

julia> 1.5x^2 - .5x + 1
13.0
```

Es macht das Schreiben von exponentiellen Funktionen auch eleganter:

```jldoctest numeric-coefficients
julia> 2^2x
64
```

Die Priorität von numerischen Literal-Koeffizienten ist etwas niedriger als die von unären Operatoren wie der Negation. Daher wird `-2x` als `(-2) * x` interpretiert und `√2x` als `(√2) * x`. Numerische Literal-Koeffizienten werden jedoch ähnlich wie unäre Operatoren interpretiert, wenn sie mit Exponentiation kombiniert werden. Zum Beispiel wird `2^3x` als `2^(3x)` interpretiert, und `2x^3` wird als `2*(x^3)` interpretiert.

Zahlenliterale funktionieren auch als Koeffizienten für in Klammern gesetzte Ausdrücke:

```jldoctest numeric-coefficients
julia> 2(x-1)^2 - 3(x-1) + 1
3
```

!!! note
    Die Priorität von numerischen Literal-Koeffizienten, die für die implizite Multiplikation verwendet werden, ist höher als die anderer binärer Operatoren wie Multiplikation (`*`) und Division (`/`, `\` und `//`). Das bedeutet zum Beispiel, dass `1 / 2im` gleich `-0.5im` und `6 // 2(2 + 1)` gleich `1 // 1` ist.


Zusätzlich können in Klammern gesetzte Ausdrücke als Koeffizienten für Variablen verwendet werden, was die Multiplikation des Ausdrucks mit der Variablen impliziert:

```jldoctest numeric-coefficients
julia> (x-1)x
6
```

Weder die Juxtaposition von zwei in Klammern gesetzten Ausdrücken noch das Platzieren einer Variablen vor einem in Klammern gesetzten Ausdruck können jedoch verwendet werden, um Multiplikation zu implizieren:

```jldoctest numeric-coefficients
julia> (x-1)(x+1)
ERROR: MethodError: objects of type Int64 are not callable

julia> x(x+1)
ERROR: MethodError: objects of type Int64 are not callable
```

Beide Ausdrücke werden als Funktionsanwendung interpretiert: Jeder Ausdruck, der kein numerisches Literal ist und unmittelbar von einer Klammer gefolgt wird, wird als Funktion interpretiert, die auf die Werte in den Klammern angewendet wird (siehe [Functions](@ref) für weitere Informationen zu Funktionen). Daher tritt in beiden Fällen ein Fehler auf, da der linke Wert keine Funktion ist.

Die oben genannten syntaktischen Verbesserungen reduzieren erheblich das visuelle Rauschen, das beim Schreiben gängiger mathematischer Formeln entsteht. Beachten Sie, dass kein Leerzeichen zwischen einem numerischen Literal-Koeffizienten und der Kennung oder dem in Klammern gesetzten Ausdruck, den er multipliziert, stehen darf.

### Syntax Conflicts

Juxtaposed literal-Koeffizienten-Syntax kann mit einigen numerischen Literal-Syntaxen in Konflikt geraten: hexadezimale, oktale und binäre Ganzzahl-Literale sowie Ingenieurnotation für Gleitkomma-Literale. Hier sind einige Situationen, in denen syntaktische Konflikte auftreten:

  * Der hexadezimale Ganzzahl-Literal-Ausdruck `0xff` könnte als das numerische Literal `0` interpretiert werden, das mit der Variablen `xff` multipliziert wird. Ähnliche Mehrdeutigkeiten treten bei oktalen und binären Literalen wie `0o777` oder `0b01001010` auf.
  * Der Gleitkomma-Literal-Ausdruck `1e10` könnte als die numerische Literal `1` interpretiert werden, multipliziert mit der Variablen `e10`, und ähnlich mit der entsprechenden `E`-Form.
  * Der 32-Bit-Gleitkomma-Literal-Ausdruck `1.5f22` könnte als die numerische Konstante `1.5` interpretiert werden, die mit der Variablen `f22` multipliziert wird.

In allen Fällen wird die Mehrdeutigkeit zugunsten der Interpretation als numerische Literale aufgelöst:

  * Ausdrücke, die mit `0x`/`0o`/`0b` beginnen, sind immer hexadezimale/octalische/binäre Literale.
  * Ausdrücke, die mit einer numerischen Konstante beginnen, gefolgt von `e` oder `E`, sind immer Gleitkomma-Konstanten.
  * Ausdrücke, die mit einem numerischen Literal beginnen, gefolgt von `f`, sind immer 32-Bit-Gleitkomma-Literale.

Im Gegensatz zu `E`, das aus historischen Gründen in numerischen Literalen `e` entspricht, ist `F` nur ein weiterer Buchstabe und verhält sich nicht wie `f` in numerischen Literalen. Daher werden Ausdrücke, die mit einem numerischen Literal gefolgt von `F` beginnen, als das numerische Literal multipliziert mit einer Variablen interpretiert, was bedeutet, dass zum Beispiel `1.5F22` gleich `1.5 * F22` ist.

## Literal zero and one

Julia bietet Funktionen, die den literalen 0 und 1 entsprechend einem angegebenen Typ oder dem Typ einer gegebenen Variablen zurückgeben.

| Function          | Description                                      |
|:----------------- |:------------------------------------------------ |
| [`zero(x)`](@ref) | Literal zero of type `x` or type of variable `x` |
| [`one(x)`](@ref)  | Literal one of type `x` or type of variable `x`  |

Diese Funktionen sind nützlich in [Numeric Comparisons](@ref), um Overhead durch unnötige [type conversion](@ref conversion-and-promotion) zu vermeiden.

Beispiele:

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
