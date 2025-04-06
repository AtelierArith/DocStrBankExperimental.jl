# Control Flow

Julia bietet eine Vielzahl von Kontrollflusskonstrukten:

  * [Compound Expressions](@ref man-compound-expressions): `begin` und `;`.
  * [Conditional Evaluation](@ref man-conditional-evaluation): `wenn`-`sonst wenn`-`ansonsten` und `?:` (ternärer Operator).
  * [Short-Circuit Evaluation](@ref): logische Operatoren `&&` („und“) und `||` („oder“) sowie verkettete Vergleiche.
  * [Repeated Evaluation: Loops](@ref man-loops): `während` und `für`.
  * [Exception Handling](@ref): `versuchen`-`fangen`, [`error`](@ref) und [`throw`](@ref).
  * [Tasks (aka Coroutines)](@ref man-tasks): [`yieldto`](@ref).

Die ersten fünf Kontrollflussmechanismen sind in Hochsprachen standardmäßig. [`Task`](@ref) sind nicht so standardmäßig: sie bieten nicht-lokalen Kontrollfluss, was es ermöglicht, zwischen vorübergehend angehaltenen Berechnungen zu wechseln. Dies ist ein mächtiges Konstrukt: sowohl Ausnahmebehandlung als auch kooperatives Multitasking werden in Julia mithilfe von Aufgaben implementiert. Die alltägliche Programmierung erfordert keine direkte Nutzung von Aufgaben, aber bestimmte Probleme können viel einfacher gelöst werden, indem man Aufgaben verwendet.

## [Compound Expressions](@id man-compound-expressions)

Manchmal ist es praktisch, einen einzelnen Ausdruck zu haben, der mehrere Unterausdrücke der Reihe nach auswertet und den Wert des letzten Unterausdrucks als seinen Wert zurückgibt. Es gibt zwei Julia-Konstrukte, die dies erreichen: `begin`-Blöcke und `;`-Ketten. Der Wert beider zusammengesetzter Ausdruckskonstrukte ist der des letzten Unterausdrucks. Hier ist ein Beispiel für einen `begin`-Block:

```jldoctest
julia> z = begin
           x = 1
           y = 2
           x + y
       end
3
```

Da diese relativ kleine, einfache Ausdrücke sind, könnten sie leicht in eine einzige Zeile geschrieben werden, wo die `;`-Kettensyntax nützlich ist:

```jldoctest
julia> z = (x = 1; y = 2; x + y)
3
```

Diese Syntax ist besonders nützlich mit der prägnanten einzeiligen Funktionsdefinitionsform, die in [Functions](@ref man-functions) eingeführt wurde. Obwohl es typisch ist, gibt es keine Anforderung, dass `begin`-Blöcke mehrzeilig oder dass `;`-Ketten einzeilig sind:

```jldoctest
julia> begin x = 1; y = 2; x + y end
3

julia> (x = 1;
        y = 2;
        x + y)
3
```

## [Conditional Evaluation](@id man-conditional-evaluation)

Bedingte Auswertung ermöglicht es, Teile des Codes je nach Wert eines booleschen Ausdrucks zu bewerten oder nicht zu bewerten. Hier ist die Anatomie der `if`-`elseif`-`else`-Bedingungssyntax:

```julia
if x < y
    println("x is less than y")
elseif x > y
    println("x is greater than y")
else
    println("x is equal to y")
end
```

Wenn der Bedingungsausdruck `x < y` `wahr` ist, wird der entsprechende Block ausgewertet; andernfalls wird der Bedingungsausdruck `x > y` ausgewertet, und wenn dieser `wahr` ist, wird der entsprechende Block ausgewertet; wenn keiner der Ausdrücke `wahr` ist, wird der `else`-Block ausgewertet. Hier ist es in Aktion:

```jldoctest
julia> function test(x, y)
           if x < y
               println("x is less than y")
           elseif x > y
               println("x is greater than y")
           else
               println("x is equal to y")
           end
       end
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

Die `elseif`- und `else`-Blöcke sind optional, und es können so viele `elseif`-Blöcke verwendet werden, wie gewünscht. Die Bedingungsausdrücke im `if`-`elseif`-`else`-Konstrukt werden ausgewertet, bis der erste Ausdruck `true` ergibt, wonach der zugehörige Block ausgewertet wird und keine weiteren Bedingungsausdrücke oder Blöcke ausgewertet werden.

`if`-Blöcke sind "undicht", d.h. sie führen keinen lokalen Geltungsbereich ein. Das bedeutet, dass neue Variablen, die innerhalb der `if`-Klauseln definiert werden, nach dem `if`-Block verwendet werden können, auch wenn sie vorher nicht definiert wurden. Wir hätten die `test`-Funktion oben also auch so definieren können als

```jldoctest
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           else
               relation = "greater than"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(2, 1)
x is greater than y.
```

Die Variable `relation` wird innerhalb des `if`-Blocks deklariert, aber außerhalb verwendet. Wenn Sie jedoch von diesem Verhalten abhängen, stellen Sie sicher, dass alle möglichen Codepfade einen Wert für die Variable definieren. Die folgende Änderung an der obigen Funktion führt zu einem Laufzeitfehler.

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(1,2)
x is less than y.

julia> test(2,1)
ERROR: UndefVarError: `relation` not defined in local scope
Stacktrace:
 [1] test(::Int64, ::Int64) at ./none:7
```

`if`-Blöcke geben ebenfalls einen Wert zurück, was für Benutzer, die aus vielen anderen Sprachen kommen, unintuitiv erscheinen mag. Dieser Wert ist einfach der Rückgabewert der letzten ausgeführten Anweisung in dem gewählten Zweig, sodass

```jldoctest
julia> x = 3
3

julia> if x > 0
           "positive!"
       else
           "negative..."
       end
"positive!"
```

Beachten Sie, dass sehr kurze bedingte Anweisungen (Einzeiler) häufig in Julia mithilfe von Kurzschlussauswertung ausgedrückt werden, wie im nächsten Abschnitt beschrieben.

Im Gegensatz zu C, MATLAB, Perl, Python und Ruby – aber wie Java und einige andere strengere, typisierte Sprachen – ist es ein Fehler, wenn der Wert eines bedingten Ausdrucks etwas anderes als `true` oder `false` ist:

```jldoctest
julia> if 1
           println("true")
       end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

Dieser Fehler zeigt an, dass die Bedingung vom falschen Typ war: [`Int64`](@ref) anstelle des erforderlichen [`Bool`](@ref).

Der sogenannte "ternäre Operator", `?:`, steht in engem Zusammenhang mit der `if`-`elseif`-`else`-Syntax, wird jedoch dort verwendet, wo eine bedingte Auswahl zwischen einzelnen Ausdruckswerten erforderlich ist, im Gegensatz zur bedingten Ausführung längerer Codeblöcke. Er trägt seinen Namen, weil er der einzige Operator in den meisten Sprachen ist, der drei Operanden benötigt:

```julia
a ? b : c
```

Der Ausdruck `a`, vor dem `?`, ist ein Bedingungsausdruck, und die ternäre Operation bewertet den Ausdruck `b`, vor dem `:`, wenn die Bedingung `a` `wahr` ist oder den Ausdruck `c`, nach dem `:`, wenn sie `falsch` ist. Beachten Sie, dass die Leerzeichen um `?` und `:` obligatorisch sind: Ein Ausdruck wie `a?b:c` ist kein gültiger ternärer Ausdruck (aber ein Zeilenumbruch ist nach sowohl dem `?` als auch dem `:` akzeptabel).

Der einfachste Weg, dieses Verhalten zu verstehen, ist, ein Beispiel zu sehen. Im vorherigen Beispiel wird der `println`-Aufruf von allen drei Zweigen geteilt: Die einzige echte Wahl ist, welchen Literal-String man drucken möchte. Dies könnte prägnanter mit dem ternären Operator geschrieben werden. Der Klarheit halber versuchen wir zuerst eine zweigeteilte Version:

```jldoctest
julia> x = 1; y = 2;

julia> println(x < y ? "less than" : "not less than")
less than

julia> x = 1; y = 0;

julia> println(x < y ? "less than" : "not less than")
not less than
```

Wenn der Ausdruck `x < y` wahr ist, bewertet der gesamte ternäre Operator-Ausdruck den String `"less than"` und andernfalls bewertet er den String `"not less than"`. Das ursprüngliche Drei-Wege-Beispiel erfordert das Verketten mehrerer Verwendungen des ternären Operators:

```jldoctest
julia> test(x, y) = println(x < y ? "x is less than y"    :
                            x > y ? "x is greater than y" : "x is equal to y")
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

Um das Verketten zu erleichtern, assoziiert der Operator von rechts nach links.

Es ist bedeutend, dass wie `if`-`elseif`-`else` die Ausdrücke vor und nach dem `:` nur ausgewertet werden, wenn der Bedingungsausdruck zu `true` oder `false` ausgewertet wird, entsprechend:

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> 1 < 2 ? v("yes") : v("no")
yes
"yes"

julia> 1 > 2 ? v("yes") : v("no")
no
"no"
```

## Short-Circuit Evaluation

Die `&&`- und `||`-Operatoren in Julia entsprechen den logischen "und"- und "oder"-Operationen und werden typischerweise für diesen Zweck verwendet. Sie haben jedoch eine zusätzliche Eigenschaft der *Kurzschluss*-Auswertung: Sie werten ihr zweites Argument nicht unbedingt aus, wie unten erklärt. (Es gibt auch bitweise `&`- und `|`-Operatoren, die als logisches "und" und "oder" *ohne* Kurzschlussverhalten verwendet werden können, aber beachten Sie, dass `&` und `|` eine höhere Priorität als `&&` und `||` für die Auswertungsreihenfolge haben.)

Die Kurzschlussauswertung ist der bedingten Auswertung sehr ähnlich. Das Verhalten findet sich in den meisten imperativen Programmiersprachen, die die booleschen Operatoren `&&` und `||` verwenden: In einer Reihe von booleschen Ausdrücken, die durch diese Operatoren verbunden sind, werden nur die minimal erforderlichen Ausdrücke ausgewertet, um den endgültigen booleschen Wert der gesamten Kette zu bestimmen. Einige Sprachen (wie Python) bezeichnen sie als `and` (`&&`) und `or` (`||`). Dies bedeutet ausdrücklich, dass:

  * In dem Ausdruck `a && b` wird der Teilausdruck `b` nur ausgewertet, wenn `a` zu `true` ausgewertet wird.
  * In dem Ausdruck `a || b` wird der Teilausdruck `b` nur ausgewertet, wenn `a` zu `false` ausgewertet wird.

Die Begründung ist, dass `a && b` `false` sein muss, wenn `a` `false` ist, unabhängig vom Wert von `b`, und ebenso muss der Wert von `a || b` `true` sein, wenn `a` `true` ist, unabhängig vom Wert von `b`. Sowohl `&&` als auch `||` assoziieren sich nach rechts, aber `&&` hat eine höhere Priorität als `||`. Es ist einfach, mit diesem Verhalten zu experimentieren:

```jldoctest tandf
julia> t(x) = (println(x); true)
t (generic function with 1 method)

julia> f(x) = (println(x); false)
f (generic function with 1 method)

julia> t(1) && t(2)
1
2
true

julia> t(1) && f(2)
1
2
false

julia> f(1) && t(2)
1
false

julia> f(1) && f(2)
1
false

julia> t(1) || t(2)
1
true

julia> t(1) || f(2)
1
true

julia> f(1) || t(2)
1
2
true

julia> f(1) || f(2)
1
2
false
```

Sie können auf die gleiche Weise leicht mit der Assoziativität und Priorität verschiedener Kombinationen von `&&` und `||` Operatoren experimentieren.

Dieses Verhalten wird häufig in Julia verwendet, um eine Alternative zu sehr kurzen `if`-Anweisungen zu bilden. Anstelle von `if <cond> <statement> end` kann man `<cond> && <statement>` schreiben (was man lesen könnte als: <cond> *und dann* <statement>). Ähnlich kann man anstelle von `if ! <cond> <statement> end` `<cond> || <statement>` schreiben (was man lesen könnte als: <cond> *oder sonst* <statement>).

Zum Beispiel könnte eine rekursive Fakultätsroutine wie folgt definiert werden:

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function fact(n::Int)
           n >= 0 || error("n must be non-negative")
           n == 0 && return 1
           n * fact(n-1)
       end
fact (generic function with 1 method)

julia> fact(5)
120

julia> fact(0)
1

julia> fact(-1)
ERROR: n must be non-negative
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fact(::Int64) at ./none:2
 [3] top-level scope
```

Boolesche Operationen *ohne* Kurzschlussauswertung können mit den bitweisen Booleschen Operatoren durchgeführt werden, die in [Mathematical Operations and Elementary Functions](@ref) eingeführt wurden: `&` und `|`. Dies sind normale Funktionen, die zufällig die Syntax von Infix-Operatoren unterstützen, aber immer ihre Argumente auswerten:

```jldoctest tandf
julia> f(1) & t(2)
1
2
false

julia> t(1) | t(2)
1
2
true
```

Genau wie Bedingungsausdrücke, die in `if`, `elseif` oder dem ternären Operator verwendet werden, müssen die Operanden von `&&` oder `||` boolesche Werte (`true` oder `false`) sein. Die Verwendung eines nicht-boole'schen Wertes an einer Stelle außer dem letzten Eintrag in einer bedingten Kette ist ein Fehler:

```jldoctest
julia> 1 && true
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

Andererseits kann am Ende einer bedingten Kette jeder Ausdruck verwendet werden. Er wird ausgewertet und zurückgegeben, abhängig von den vorhergehenden Bedingungen:

```jldoctest
julia> true && (x = (1, 2, 3))
(1, 2, 3)

julia> false && (x = (1, 2, 3))
false
```

## [Repeated Evaluation: Loops](@id man-loops)

Es gibt zwei Konstrukte für die wiederholte Auswertung von Ausdrücken: die `while`-Schleife und die `for`-Schleife. Hier ist ein Beispiel für eine `while`-Schleife:

```jldoctest
julia> i = 1;

julia> while i <= 3
           println(i)
           global i += 1
       end
1
2
3
```

Die `while`-Schleife bewertet den Bedingungsausdruck (`i <= 3` in diesem Fall), und solange dieser `true` bleibt, wird auch der Körper der `while`-Schleife weiterhin ausgewertet. Wenn der Bedingungsausdruck `false` ist, wenn die `while`-Schleife zum ersten Mal erreicht wird, wird der Körper niemals ausgewertet.

Die `for`-Schleife erleichtert das Schreiben gängiger wiederholter Bewertungsidiome. Da das Zählen nach oben und unten, wie in der obigen `while`-Schleife, so häufig vorkommt, kann es prägnanter mit einer `for`-Schleife ausgedrückt werden:

```jldoctest
julia> for i = 1:3
           println(i)
       end
1
2
3
```

Hier ist das `1:3` ein [`range`](@ref) Objekt, das die Zahlenfolge 1, 2, 3 darstellt. Die `for`-Schleife iteriert durch diese Werte und weist jedem nacheinander die Variable `i` zu. Im Allgemeinen kann die `for`-Konstruktion über jedes "iterierbare" Objekt (oder "Container") schleifen, von einem Bereich wie `1:3` oder `1:3:13` (ein [`StepRange`](@ref), das jede 3. ganze Zahl 1, 4, 7, …, 13 angibt) bis hin zu allgemeineren Containern wie Arrays, einschließlich [iterators defined by user code](@ref man-interface-iteration) oder externen Paketen. Für Container, die keine Bereiche sind, wird typischerweise das alternative (aber vollständig äquivalente) Schlüsselwort `in` oder `∈` anstelle von `=` verwendet, da es den Code klarer lesbar macht:

```jldoctest
julia> for i in [1,4,0]
           println(i)
       end
1
4
0

julia> for s ∈ ["foo","bar","baz"]
           println(s)
       end
foo
bar
baz
```

In späteren Abschnitten des Handbuchs werden verschiedene Arten von iterierbaren Containern eingeführt und diskutiert (siehe z. B. [Multi-dimensional Arrays](@ref man-multi-dim-arrays)).

Eine ziemlich wichtige Unterscheidung zwischen der vorherigen `while`-Schleifenform und der `for`-Schleifenform ist der Geltungsbereich, in dem die Variable sichtbar ist. Eine `for`-Schleife führt immer eine neue Iterationsvariable in ihrem Körper ein, unabhängig davon, ob eine Variable mit demselben Namen im umgebenden Geltungsbereich existiert. Das bedeutet, dass `i` einerseits nicht vor der Schleife deklariert werden muss. Andererseits wird sie außerhalb der Schleife nicht sichtbar sein, noch wird eine außerhalb befindliche Variable mit demselben Namen betroffen sein. Sie benötigen entweder eine neue interaktive Sitzungsinstanz oder einen anderen Variablennamen, um dies zu testen:

```jldoctest
julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
ERROR: UndefVarError: `j` not defined in `Main`
```

```jldoctest
julia> j = 0;

julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
0
```

Verwenden Sie `for outer`, um das spätere Verhalten zu ändern und eine vorhandene lokale Variable wiederzuverwenden.

Siehe [Scope of Variables](@ref scope-of-variables) für eine detaillierte Erklärung des Variablenbereichs, [`outer`](@ref), und wie es in Julia funktioniert.

Es ist manchmal praktisch, die Wiederholung einer `while`-Schleife zu beenden, bevor die Testbedingung falsch wird, oder das Iterieren in einer `for`-Schleife zu stoppen, bevor das Ende des iterierbaren Objekts erreicht ist. Dies kann mit dem Schlüsselwort `break` erreicht werden:

```jldoctest
julia> i = 1;

julia> while true
           println(i)
           if i >= 3
               break
           end
           global i += 1
       end
1
2
3

julia> for j = 1:1000
           println(j)
           if j >= 3
               break
           end
       end
1
2
3
```

Ohne das `break`-Schlüsselwort würde die oben stehende `while`-Schleife von selbst niemals enden, und die `for`-Schleife würde bis zu 1000 iterieren. Beide Schleifen werden vorzeitig mit `break` verlassen.

In anderen Umständen ist es nützlich, eine Iteration zu stoppen und sofort zur nächsten überzugehen. Das Schlüsselwort `continue` erreicht dies:

```jldoctest
julia> for i = 1:10
           if i % 3 != 0
               continue
           end
           println(i)
       end
3
6
9
```

Dies ist ein etwas konstruiertes Beispiel, da wir dasselbe Verhalten klarer erzeugen könnten, indem wir die Bedingung negieren und den `println`-Aufruf in den `if`-Block setzen. In der realistischen Nutzung gibt es mehr Code, der nach dem `continue` ausgewertet werden muss, und oft gibt es mehrere Punkte, von denen aus man `continue` aufruft.

Mehrere geschachtelte `for`-Schleifen können in eine einzige äußere Schleife kombiniert werden, wodurch das kartesische Produkt ihrer Iterierbaren entsteht:

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

Mit dieser Syntax können Iterierbare weiterhin auf Variablen der äußeren Schleife verweisen; z. B. ist `for i = 1:n, j = 1:i` gültig. Ein `break`-Befehl innerhalb einer solchen Schleife verlässt jedoch das gesamte Nest von Schleifen, nicht nur die innere. Beide Variablen (`i` und `j`) werden bei jedem Durchlauf der inneren Schleife auf ihre aktuellen Iterationswerte gesetzt. Daher sind Zuweisungen an `i` in nachfolgenden Iterationen nicht sichtbar:

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
           i = 0
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

Wenn dieses Beispiel umgeschrieben würde, um für jede Variable das `for`-Schlüsselwort zu verwenden, wäre die Ausgabe anders: die zweite und vierte Werte würden `0` enthalten.

Mehrere Container können gleichzeitig in einer einzigen `for`-Schleife mit [`zip`](@ref) durchlaufen werden:

```jldoctest
julia> for (j, k) in zip([1 2 3], [4 5 6 7])
           println((j,k))
       end
(1, 4)
(2, 5)
(3, 6)
```

Die Verwendung von [`zip`](@ref) erstellt einen Iterator, der ein Tupel enthält, das die Subiteratoren für die übergebenen Container enthält. Der `zip`-Iterator wird über alle Subiteratoren in der Reihenfolge iterieren und das $i$te Element jedes Subiterators in der $i$ten Iteration der `for`-Schleife auswählen. Sobald einer der Subiteratoren erschöpft ist, wird die `for`-Schleife gestoppt.

## Exception Handling

Wenn eine unerwartete Bedingung auftritt, kann eine Funktion möglicherweise keinen angemessenen Wert an ihren Aufrufer zurückgeben. In solchen Fällen ist es möglicherweise am besten, die außergewöhnliche Bedingung entweder das Programm zu beenden und eine diagnostische Fehlermeldung auszugeben, oder, wenn der Programmierer Code bereitgestellt hat, um mit solchen außergewöhnlichen Umständen umzugehen, diesen Code die entsprechenden Maßnahmen ergreifen zu lassen.

### Built-in `Exception`s

`Exception`s werden ausgelöst, wenn eine unerwartete Bedingung aufgetreten ist. Die unten aufgeführten integrierten `Exception`s unterbrechen alle den normalen Kontrollfluss.

| `Exception`                   |
|:----------------------------- |
| [`ArgumentError`](@ref)       |
| [`BoundsError`](@ref)         |
| [`CompositeException`](@ref)  |
| [`DimensionMismatch`](@ref)   |
| [`DivideError`](@ref)         |
| [`DomainError`](@ref)         |
| [`EOFError`](@ref)            |
| [`ErrorException`](@ref)      |
| [`InexactError`](@ref)        |
| [`InitError`](@ref)           |
| [`InterruptException`](@ref)  |
| `InvalidStateException`       |
| [`KeyError`](@ref)            |
| [`LoadError`](@ref)           |
| [`OutOfMemoryError`](@ref)    |
| [`ReadOnlyMemoryError`](@ref) |
| [`RemoteException`](@ref)     |
| [`MethodError`](@ref)         |
| [`OverflowError`](@ref)       |
| [`Meta.ParseError`](@ref)     |
| [`SystemError`](@ref)         |
| [`TypeError`](@ref)           |
| [`UndefRefError`](@ref)       |
| [`UndefVarError`](@ref)       |
| [`StringIndexError`](@ref)    |

Zum Beispiel wirft die [`sqrt`](@ref)-Funktion eine [`DomainError`](@ref)-Ausnahme, wenn sie auf einen negativen reellen Wert angewendet wird:

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Sie können Ihre eigenen Ausnahmen auf folgende Weise definieren:

```jldoctest
julia> struct MyCustomException <: Exception end
```

### The [`throw`](@ref) function

Ausnahmen können explizit mit [`throw`](@ref) erstellt werden. Zum Beispiel könnte eine Funktion, die nur für nicht-negative Zahlen definiert ist, so geschrieben werden, dass sie `4d61726b646f776e2e436f64652822222c20227468726f772229_40726566` eine [`DomainError`](@ref) auslöst, wenn das Argument negativ ist:

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> f(x) = x>=0 ? exp(-x) : throw(DomainError(x, "argument must be non-negative"))
f (generic function with 1 method)

julia> f(1)
0.36787944117144233

julia> f(-1)
ERROR: DomainError with -1:
argument must be non-negative
Stacktrace:
 [1] f(::Int64) at ./none:1
```

Beachten Sie, dass [`DomainError`](@ref) ohne Klammern keine Ausnahme ist, sondern eine Art von Ausnahme. Es muss aufgerufen werden, um ein `Exception`-Objekt zu erhalten:

```jldoctest
julia> typeof(DomainError(nothing)) <: Exception
true

julia> typeof(DomainError) <: Exception
false
```

Zusätzlich nehmen einige Ausnahmetypen ein oder mehrere Argumente entgegen, die für die Fehlerberichterstattung verwendet werden:

```jldoctest
julia> throw(UndefVarError(:x))
ERROR: UndefVarError: `x` not defined
```

Dieser Mechanismus kann einfach durch benutzerdefinierte Ausnahmetypen implementiert werden, die der Art und Weise folgen, wie [`UndefVarError`](@ref) geschrieben ist:

```jldoctest
julia> struct MyUndefVarError <: Exception
           var::Symbol
       end

julia> Base.showerror(io::IO, e::MyUndefVarError) = print(io, e.var, " not defined")
```

!!! note
    Wenn Sie eine Fehlermeldung schreiben, ist es bevorzugt, das erste Wort klein zu schreiben. Zum Beispiel,

    `size(A) == size(B) || throw(DimensionMismatch("Größe von A ist nicht gleich der Größe von B"))`

    wird bevorzugt gegenüber

    `size(A) == size(B) || throw(DimensionMismatch("Größe von A ist nicht gleich der Größe von B"))`.

    Es macht jedoch manchmal Sinn, den ersten Buchstaben groß zu halten, zum Beispiel wenn ein Argument für eine Funktion ein Großbuchstabe ist:

    `size(A,1) == size(B,2) || throw(DimensionMismatch("A hat die erste Dimension..."))`.


### Errors

Die [`error`](@ref)-Funktion wird verwendet, um ein [`ErrorException`](@ref) zu erzeugen, das den normalen Kontrollfluss unterbricht.

Angenommen, wir möchten die Ausführung sofort stoppen, wenn die Quadratwurzel einer negativen Zahl gezogen wird. Um dies zu tun, können wir eine unscharfe Version der [`sqrt`](@ref)-Funktion definieren, die einen Fehler auslöst, wenn ihr Argument negativ ist:

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> fussy_sqrt(x) = x >= 0 ? sqrt(x) : error("negative x not allowed")
fussy_sqrt (generic function with 1 method)

julia> fussy_sqrt(2)
1.4142135623730951

julia> fussy_sqrt(-1)
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt(::Int64) at ./none:1
 [3] top-level scope
```

Wenn `fussy_sqrt` mit einem negativen Wert von einer anderen Funktion aufgerufen wird, gibt es sofort zurück, anstatt die Ausführung der aufrufenden Funktion fortzusetzen, und zeigt die Fehlermeldung in der interaktiven Sitzung an:

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function verbose_fussy_sqrt(x)
           println("before fussy_sqrt")
           r = fussy_sqrt(x)
           println("after fussy_sqrt")
           return r
       end
verbose_fussy_sqrt (generic function with 1 method)

julia> verbose_fussy_sqrt(2)
before fussy_sqrt
after fussy_sqrt
1.4142135623730951

julia> verbose_fussy_sqrt(-1)
before fussy_sqrt
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt at ./none:1 [inlined]
 [3] verbose_fussy_sqrt(::Int64) at ./none:3
 [4] top-level scope
```

### The `try/catch` statement

Die `try/catch`-Anweisung ermöglicht es, `Exception`s zu testen und die Handhabung von Dingen, die normalerweise Ihre Anwendung zum Absturz bringen würden, elegant zu gestalten. Zum Beispiel würde die Funktion für die Quadratwurzel im folgenden Code normalerweise eine Ausnahme auslösen. Indem wir einen `try/catch`-Block darum herum platzieren, können wir das hier abmildern. Sie können entscheiden, wie Sie diese Ausnahme behandeln möchten, sei es durch Protokollierung, Rückgabe eines Platzhalterwerts oder, wie im folgenden Fall, indem wir einfach eine Aussage ausgeben. Eine Sache, über die man nachdenken sollte, wenn man entscheidet, wie man mit unerwarteten Situationen umgeht, ist, dass die Verwendung eines `try/catch`-Blocks viel langsamer ist als die Verwendung von bedingter Verzweigung, um diese Situationen zu handhaben. Unten finden Sie weitere Beispiele für die Handhabung von Ausnahmen mit einem `try/catch`-Block:

```jldoctest
julia> try
           sqrt("ten")
       catch e
           println("You should have entered a numeric value")
       end
You should have entered a numeric value
```

`try/catch`-Anweisungen ermöglichen es auch, die `Exception` in einer Variablen zu speichern. Das folgende konstruierte Beispiel berechnet die Quadratwurzel des zweiten Elements von `x`, wenn `x` indizierbar ist, andernfalls wird angenommen, dass `x` eine reelle Zahl ist, und gibt ihre Quadratwurzel zurück:

```jldoctest
julia> sqrt_second(x) = try
           sqrt(x[2])
       catch y
           if isa(y, DomainError)
               sqrt(complex(x[2], 0))
           elseif isa(y, BoundsError)
               sqrt(x)
           end
       end
sqrt_second (generic function with 1 method)

julia> sqrt_second([1 4])
2.0

julia> sqrt_second([1 -4])
0.0 + 2.0im

julia> sqrt_second(9)
3.0

julia> sqrt_second(-9)
ERROR: DomainError with -9.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Beachten Sie, dass das Symbol, das auf `catch` folgt, immer als Name für die Ausnahme interpretiert wird. Daher ist Vorsicht geboten, wenn Sie `try/catch`-Ausdrücke in einer einzigen Zeile schreiben. Der folgende Code wird *nicht* funktionieren, um den Wert von `x` im Falle eines Fehlers zurückzugeben:

```julia
try bad() catch x end
```

Stattdessen verwenden Sie ein Semikolon oder fügen Sie einen Zeilenumbruch nach `catch` ein:

```julia
try bad() catch; x end

try bad()
catch
    x
end
```

Die Macht des `try/catch`-Konstrukts liegt in der Fähigkeit, eine tief verschachtelte Berechnung sofort auf ein viel höheres Niveau im Stapel der aufrufenden Funktionen zu entwirren. Es gibt Situationen, in denen kein Fehler aufgetreten ist, aber die Fähigkeit, den Stapel zu entwirren und einen Wert an ein höheres Niveau zu übergeben, wünschenswert ist. Julia bietet die [`rethrow`](@ref), [`backtrace`](@ref), [`catch_backtrace`](@ref) und [`current_exceptions`](@ref) Funktionen für eine fortgeschrittene Fehlerbehandlung.

### `else` Clauses

!!! compat "Julia 1.8"
    Diese Funktionalität erfordert mindestens Julia 1.8.


In einigen Fällen möchte man möglicherweise nicht nur den Fehlerfall angemessen behandeln, sondern auch Code ausführen, der nur ausgeführt wird, wenn der `try`-Block erfolgreich ist. Dazu kann eine `else`-Klausel nach dem `catch`-Block angegeben werden, die ausgeführt wird, wenn zuvor kein Fehler aufgetreten ist. Der Vorteil gegenüber der Einbeziehung dieses Codes im `try`-Block besteht darin, dass weitere Fehler nicht stillschweigend von der `catch`-Klausel erfasst werden.

```julia
local x
try
    x = read("file", String)
catch
    # handle read errors
else
    # do something with x
end
```

!!! note
    Die `try`, `catch`, `else` und `finally` Klauseln führen jeweils ihre eigenen Geltungsbereiche ein, sodass eine Variable, die nur im `try` Block definiert ist, nicht von der `else` oder `finally` Klausel aus zugegriffen werden kann:

    ```jldoctest
    julia> try
               foo = 1
           catch
           else
               foo
           end
    ERROR: UndefVarError: `foo` not defined in `Main`
    Suggestion: check for spelling errors or missing imports.
    ```

    Verwenden Sie [`local` keyword](@ref local-scope) außerhalb des `try`-Blocks, um die Variable im gesamten äußeren Gültigkeitsbereich zugänglich zu machen.


### `finally` Clauses

In Code, der Zustandsänderungen vornimmt oder Ressourcen wie Dateien verwendet, gibt es typischerweise Aufräumarbeiten (wie das Schließen von Dateien), die erledigt werden müssen, wenn der Code fertig ist. Ausnahmen können diese Aufgabe potenziell komplizieren, da sie dazu führen können, dass ein Codeblock vor dem Erreichen seines normalen Endes verlässt. Das Schlüsselwort `finally` bietet eine Möglichkeit, einen bestimmten Code auszuführen, wenn ein gegebener Codeblock verlässt, unabhängig davon, wie er verlässt.

Zum Beispiel, so können wir garantieren, dass eine geöffnete Datei geschlossen wird:

```julia
f = open("file")
try
    # operate on file f
finally
    close(f)
end
```

Wenn die Kontrolle den `try`-Block verlässt (zum Beispiel aufgrund eines `return` oder einfach durch normales Beenden), wird `close(f)` ausgeführt. Wenn der `try`-Block aufgrund einer Ausnahme verlässt, wird die Ausnahme weiterhin propagiert. Ein `catch`-Block kann auch mit `try` und `finally` kombiniert werden. In diesem Fall wird der `finally`-Block ausgeführt, nachdem der `catch`-Block den Fehler behandelt hat.

## [Tasks (aka Coroutines)](@id man-tasks)

Aufgaben sind ein Kontrollflussmerkmal, das es ermöglicht, Berechnungen flexibel auszusetzen und wieder aufzunehmen. Wir erwähnen sie hier nur der Vollständigkeit halber; für eine vollständige Diskussion siehe [Asynchronous Programming](@ref man-asynchronous).
