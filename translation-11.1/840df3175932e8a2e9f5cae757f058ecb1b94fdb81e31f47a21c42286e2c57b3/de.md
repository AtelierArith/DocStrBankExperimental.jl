# Complex and Rational Numbers

Julia umfasst vordefinierte Typen für sowohl komplexe als auch rationale Zahlen und unterstützt alle standardmäßigen [Mathematical Operations and Elementary Functions](@ref) auf ihnen. [Conversion and Promotion](@ref conversion-and-promotion) sind so definiert, dass Operationen an jeder Kombination von vordefinierten numerischen Typen, ob primitiv oder zusammengesetzt, wie erwartet funktionieren.

## Complex Numbers

Die globale Konstante [`im`](@ref) ist an die komplexe Zahl *i* gebunden, die die Hauptwurzel von -1 darstellt. (Die Verwendung von Mathematikern `i` oder Ingenieuren `j` für diese globale Konstante wurde abgelehnt, da sie so beliebte Indexvariablennamen sind.) Da Julia numerische Literale erlaubt, die [juxtaposed with identifiers as coefficients](@ref man-numeric-literal-coefficients) sind, reicht diese Bindung aus, um eine bequeme Syntax für komplexe Zahlen bereitzustellen, ähnlich der traditionellen mathematischen Notation:

```jldoctest
julia> 1+2im
1 + 2im
```

Sie können alle standardmäßigen arithmetischen Operationen mit komplexen Zahlen durchführen:

```jldoctest
julia> (1 + 2im)*(2 - 3im)
8 + 1im

julia> (1 + 2im)/(1 - 2im)
-0.6 + 0.8im

julia> (1 + 2im) + (1 - 2im)
2 + 0im

julia> (-3 + 2im) - (5 - 1im)
-8 + 3im

julia> (-1 + 2im)^2
-3 - 4im

julia> (-1 + 2im)^2.5
2.729624464784009 - 6.9606644595719im

julia> (-1 + 2im)^(1 + 1im)
-0.27910381075826657 + 0.08708053414102428im

julia> 3(2 - 5im)
6 - 15im

julia> 3(2 - 5im)^2
-63 - 60im

julia> 3(2 - 5im)^-1.0
0.20689655172413793 + 0.5172413793103449im
```

Der Promotionsmechanismus stellt sicher, dass Kombinationen von Operanden unterschiedlicher Typen einfach funktionieren:

```jldoctest
julia> 2(1 - 1im)
2 - 2im

julia> (2 + 3im) - 1
1 + 3im

julia> (1 + 2im) + 0.5
1.5 + 2.0im

julia> (2 + 3im) - 0.5im
2.0 + 2.5im

julia> 0.75(1 + 2im)
0.75 + 1.5im

julia> (2 + 3im) / 2
1.0 + 1.5im

julia> (1 - 3im) / (2 + 2im)
-0.5 - 1.0im

julia> 2im^2
-2 + 0im

julia> 1 + 3/4im
1.0 - 0.75im
```

Beachten Sie, dass `3/4im == 3/(4*im) == -(3/4*im)` ist, da ein literaler Koeffizient enger bindet als die Division.

Standardfunktionen zur Manipulation komplexer Werte sind verfügbar:

```jldoctest
julia> z = 1 + 2im
1 + 2im

julia> real(1 + 2im) # real part of z
1

julia> imag(1 + 2im) # imaginary part of z
2

julia> conj(1 + 2im) # complex conjugate of z
1 - 2im

julia> abs(1 + 2im) # absolute value of z
2.23606797749979

julia> abs2(1 + 2im) # squared absolute value
5

julia> angle(1 + 2im) # phase angle in radians
1.1071487177940904
```

Wie gewohnt ist der Betrag ([`abs`](@ref)) einer komplexen Zahl ihre Entfernung von Null. [`abs2`](@ref) gibt das Quadrat des Betrags zurück und ist besonders nützlich für komplexe Zahlen, da es das Ziehen einer Quadratwurzel vermeidet. [`angle`](@ref) gibt den Phasenwinkel in Bogenmaß zurück (auch bekannt als die *Argument*- oder *arg*-Funktion). Das gesamte Spektrum anderer [Elementary Functions](@ref) ist ebenfalls für komplexe Zahlen definiert:

```jldoctest
julia> sqrt(1im)
0.7071067811865476 + 0.7071067811865475im

julia> sqrt(1 + 2im)
1.272019649514069 + 0.7861513777574233im

julia> cos(1 + 2im)
2.0327230070196656 - 3.0518977991517997im

julia> exp(1 + 2im)
-1.1312043837568135 + 2.4717266720048188im

julia> sinh(1 + 2im)
-0.4890562590412937 + 1.4031192506220405im
```

Beachten Sie, dass mathematische Funktionen typischerweise reelle Werte zurückgeben, wenn sie auf reelle Zahlen angewendet werden, und komplexe Werte, wenn sie auf komplexe Zahlen angewendet werden. Zum Beispiel verhält sich [`sqrt`](@ref) unterschiedlich, wenn sie auf `-1` im Vergleich zu `-1 + 0im` angewendet wird, obwohl `-1 == -1 + 0im` ist:

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]

julia> sqrt(-1 + 0im)
0.0 + 1.0im
```

Die [literal numeric coefficient notation](@ref man-numeric-literal-coefficients) funktioniert nicht, wenn man eine komplexe Zahl aus Variablen konstruiert. Stattdessen muss die Multiplikation ausdrücklich ausgeschrieben werden:

```jldoctest
julia> a = 1; b = 2; a + b*im
1 + 2im
```

Es wird jedoch *nicht* empfohlen. Verwenden Sie stattdessen die effizientere [`complex`](@ref)-Funktion, um einen komplexen Wert direkt aus seinen reellen und imaginären Teilen zu erstellen:

```jldoctest
julia> a = 1; b = 2; complex(a, b)
1 + 2im
```

Dieser Aufbau vermeidet die Multiplikations- und Additionsoperationen.

[`Inf`](@ref) und [`NaN`](@ref) verbreiten sich durch komplexe Zahlen in den reellen und imaginären Teilen einer komplexen Zahl, wie im Abschnitt [Special floating-point values](@ref) beschrieben:

```jldoctest
julia> 1 + Inf*im
1.0 + Inf*im

julia> 1 + NaN*im
1.0 + NaN*im
```

## Rational Numbers

Julia hat einen rationalen Zahlentyp, um exakte Verhältnisse von Ganzzahlen darzustellen. Rationale Zahlen werden mit dem [`//`](@ref) Operator erstellt:

```jldoctest
julia> 2//3
2//3
```

Wenn Zähler und Nenner eines rationalen Ausdrucks gemeinsame Faktoren haben, werden sie auf die niedrigsten Terme reduziert, sodass der Nenner nicht negativ ist:

```jldoctest
julia> 6//9
2//3

julia> -4//8
-1//2

julia> 5//-15
-1//3

julia> -4//-12
1//3
```

Diese normierte Form für ein Verhältnis von Ganzzahlen ist einzigartig, sodass die Gleichheit rationaler Werte getestet werden kann, indem die Gleichheit des Zählers und des Nenners überprüft wird. Der standardisierte Zähler und Nenner eines rationalen Wertes kann mit den Funktionen [`numerator`](@ref) und [`denominator`](@ref) extrahiert werden:

```jldoctest
julia> numerator(2//3)
2

julia> denominator(2//3)
3
```

Ein direkter Vergleich von Zähler und Nenner ist im Allgemeinen nicht erforderlich, da die standardmäßigen arithmetischen und Vergleichsoperationen für rationale Werte definiert sind:

```jldoctest
julia> 2//3 == 6//9
true

julia> 2//3 == 9//27
false

julia> 3//7 < 1//2
true

julia> 3//4 > 2//3
true

julia> 2//4 + 1//6
2//3

julia> 5//12 - 1//4
1//6

julia> 5//8 * 3//12
5//32

julia> 6//5 / 10//7
21//25
```

Rationale können leicht in Fließkommazahlen umgewandelt werden:

```jldoctest
julia> float(3//4)
0.75
```

Die Umwandlung von rationalen Zahlen in Gleitkommazahlen respektiert die folgende Identität für alle ganzzahligen Werte von `a` und `b`, außer wenn `a==0 && b <= 0`:

```jldoctest
julia> a = 1; b = 2;

julia> isequal(float(a//b), a/b)
true

julia> a, b = 0, 0
(0, 0)

julia> float(a//b)
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]

julia> a/b
NaN

julia> a, b = 0, -1
(0, -1)

julia> float(a//b), a/b
(0.0, -0.0)
```

Unendliche rationale Werte zu konstruieren ist akzeptabel:

```jldoctest
julia> 5//0
1//0

julia> x = -3//0
-1//0

julia> typeof(x)
Rational{Int64}
```

Versuche, einen [`NaN`](@ref) rationalen Wert zu konstruieren, der jedoch ungültig ist:

```jldoctest
julia> 0//0
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]
```

Wie gewohnt macht das Promotionssystem Interaktionen mit anderen numerischen Typen mühelos:

```jldoctest
julia> 3//5 + 1
8//5

julia> 3//5 - 0.5
0.09999999999999998

julia> 2//7 * (1 + 2im)
2//7 + 4//7*im

julia> 2//7 * (1.5 + 2im)
0.42857142857142855 + 0.5714285714285714im

julia> 3//2 / (1 + 2im)
3//10 - 3//5*im

julia> 1//2 + 2im
1//2 + 2//1*im

julia> 1 + 2//3im
1//1 - 2//3*im

julia> 0.5 == 1//2
true

julia> 0.33 == 1//3
false

julia> 0.33 < 1//3
true

julia> 1//3 - 0.33
0.0033333333333332993
```
