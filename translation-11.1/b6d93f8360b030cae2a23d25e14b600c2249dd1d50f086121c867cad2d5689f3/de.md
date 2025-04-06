# [Functions](@id man-functions)

In Julia ist eine Funktion ein Objekt, das ein Tupel von Argumentwerten auf einen Rückgabewert abbildet. Julia-Funktionen sind keine reinen mathematischen Funktionen, da sie den globalen Zustand des Programms ändern und von ihm beeinflusst werden können. Die grundlegende Syntax zur Definition von Funktionen in Julia ist:

```jldoctest
julia> function f(x, y)
           x + y
       end
f (generic function with 1 method)
```

Diese Funktion akzeptiert zwei Argumente `x` und `y` und gibt den Wert des letzten ausgewerteten Ausdrucks zurück, der `x + y` ist.

Es gibt eine zweite, kürzere Syntax zur Definition einer Funktion in Julia. Die oben demonstrierte traditionelle Funktionsdeklarationssyntax ist äquivalent zu der folgenden kompakten "Zuweisungsform":

```jldoctest fofxy
julia> f(x, y) = x + y
f (generic function with 1 method)
```

Im dem Zuweisungsformular muss der Körper der Funktion ein einzelner Ausdruck sein, obwohl er ein zusammengesetzter Ausdruck sein kann (siehe [Compound Expressions](@ref man-compound-expressions)). Kurze, einfache Funktionsdefinitionen sind in Julia üblich. Die kurze Funktionssyntax ist daher ziemlich idiomatisch und reduziert sowohl das Tippen als auch das visuelle Rauschen erheblich.

Eine Funktion wird mit der traditionellen Klammer-Syntax aufgerufen:

```jldoctest fofxy
julia> f(2, 3)
5
```

Ohne Klammern bezieht sich der Ausdruck `f` auf das Funktionsobjekt und kann wie jeder andere Wert weitergegeben werden:

```jldoctest fofxy
julia> g = f;

julia> g(2, 3)
5
```

Wie bei Variablen kann Unicode auch für Funktionsnamen verwendet werden:

```jldoctest
julia> ∑(x, y) = x + y
∑ (generic function with 1 method)

julia> ∑(2, 3)
5
```

## [Argument Passing Behavior](@id man-argument-passing)

Die Argumente von Julia-Funktionen folgen einer Konvention, die manchmal als "Pass-by-Sharing" bezeichnet wird, was bedeutet, dass Werte nicht kopiert werden, wenn sie an Funktionen übergeben werden. Die Funktionsargumente selbst fungieren als neue Variablen *Bindungen* (neue "Namen", die auf Werte verweisen können), ähnlich wie [assignments](@ref man-assignment-expressions) `argument_name = argument_value`, sodass die Objekte, auf die sie verweisen, identisch mit den übergebenen Werten sind. Änderungen an veränderbaren Werten (wie `Array`s), die innerhalb einer Funktion vorgenommen werden, sind für den Aufrufer sichtbar. (Dies ist dasselbe Verhalten, das in Scheme, den meisten Lisps, Python, Ruby und Perl sowie anderen dynamischen Sprachen zu finden ist.)

Zum Beispiel, in der Funktion

```julia
function f(x, y)
    x[1] = 42    # mutates x
    y = 7 + y    # new binding for y, no mutation
    return y
end
```

Die Anweisung `x[1] = 42` *verändert* das Objekt `x`, und daher wird diese Änderung *sichtbar* im Array, das vom Aufrufer für dieses Argument übergeben wurde. Auf der anderen Seite ändert die Zuweisung `y = 7 + y` die *Bindung* ("Name") `y`, sodass sie auf einen neuen Wert `7 + y` verweist, anstatt das *ursprüngliche* Objekt, auf das `y` verweist, zu verändern, und daher *ändert* sie *nicht* das entsprechende Argument, das vom Aufrufer übergeben wurde. Dies kann gesehen werden, wenn wir `f(x, y)` aufrufen:

```julia-repl
julia> a = [4, 5, 6]
3-element Vector{Int64}:
 4
 5
 6

julia> b = 3
3

julia> f(a, b) # returns 7 + b == 10
10

julia> a  # a[1] is changed to 42 by f
3-element Vector{Int64}:
 42
  5
  6

julia> b  # not changed
3
```

Als gängige Konvention in Julia (keine syntaktische Anforderung) würde eine solche Funktion [typically be named `f!(x, y)`](@ref man-punctuation) anstelle von `f(x, y)` verwendet, um am Aufrufort visuell zu erinnern, dass mindestens eines der Argumente (oft das erste) verändert wird.

!!! warning "Shared memory between arguments"
    Das Verhalten einer mutierenden Funktion kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt, eine Situation, die als Aliasing bekannt ist (z. B. wenn eines eine Ansicht des anderen ist). Es liegt in der Verantwortung des Aufrufers, bei solchen Eingaben für ein korrektes Verhalten zu sorgen, es sei denn, die Funktionsdokumentation weist ausdrücklich darauf hin, dass Aliasing das erwartete Ergebnis liefert.


## Argument-type declarations

Sie können die Typen der Funktionsargumente angeben, indem Sie `::TypeName` an den Argumentnamen anhängen, wie üblich für [Type Declarations](@ref) in Julia. Zum Beispiel berechnet die folgende Funktion [Fibonacci numbers](https://en.wikipedia.org/wiki/Fibonacci_number) rekursiv:

```
fib(n::Integer) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)
```

und die `::Integer` Spezifikation bedeutet, dass sie nur aufrufbar ist, wenn `n` ein Subtyp des [abstract](@ref man-abstract-types) `Integer` Typs ist.

Argumenttypendeklarationen **haben normalerweise keinen Einfluss auf die Leistung**: Unabhängig davon, welche Argumenttypen (falls vorhanden) deklariert sind, kompiliert Julia eine spezialisierte Version der Funktion für die tatsächlichen Argumenttypen, die vom Aufrufer übergeben werden. Zum Beispiel wird der Aufruf von `fib(1)` die Kompilierung einer spezialisierten Version von `fib` auslösen, die speziell für `Int`-Argumente optimiert ist und dann wiederverwendet wird, wenn `fib(7)` oder `fib(15)` aufgerufen werden. (Es gibt seltene Ausnahmen, bei denen eine Argumenttypdeklaration zusätzliche Compiler-Spezialisierungen auslösen kann; siehe: [Be aware of when Julia avoids specializing](@ref).) Die häufigsten Gründe, Argumenttypen in Julia zu deklarieren, sind stattdessen:

  * **Dispatch:** Wie in [Methods](@ref) erklärt, können Sie verschiedene Versionen ("Methoden") einer Funktion für unterschiedliche Argumenttypen haben, wobei die Argumenttypen verwendet werden, um zu bestimmen, welche Implementierung für welche Argumente aufgerufen wird. Zum Beispiel könnten Sie einen völlig anderen Algorithmus implementieren `fib(x::Number) = ...`, der für jeden `Number`-Typ funktioniert, indem Sie [Binet's formula](https://en.wikipedia.org/wiki/Fibonacci_number#Binet%27s_formula) verwenden, um ihn auf nicht-ganzzahlige Werte zu erweitern.
  * **Korrektheit:** Typdeklarationen können nützlich sein, wenn Ihre Funktion nur für bestimmte Argumenttypen korrekte Ergebnisse zurückgibt. Zum Beispiel, wenn wir die Argumenttypen weglassen und `fib(n) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)` schreiben, dann würde `fib(1.5)` uns stillschweigend die unsinnige Antwort `1.0` geben.
  * **Klarheit:** Typdeklarationen können als eine Form der Dokumentation über die erwarteten Argumente dienen.

Es ist jedoch ein **häufiger Fehler, die Argumenttypen zu stark einzuschränken**, was die Anwendbarkeit der Funktion unnötig einschränken und verhindern kann, dass sie in Umständen wiederverwendet wird, die Sie nicht vorhergesehen haben. Zum Beispiel funktioniert die Funktion `fib(n::Integer)` oben ebenso gut für `Int`-Argumente (Maschinenintegers) und `BigInt`-Zahlen mit beliebiger Präzision (siehe [BigFloats and BigInts](@ref BigFloats-and-BigInts)), was besonders nützlich ist, da Fibonacci-Zahlen exponentiell schnell wachsen und schnell jeden festen Typ wie `Int` überlaufen (siehe [Overflow behavior](@ref)). Wenn wir unsere Funktion jedoch als `fib(n::Int)` deklariert hätten, wäre die Anwendung auf `BigInt` ohne Grund verhindert worden. Im Allgemeinen sollten Sie die allgemeinsten anwendbaren abstrakten Typen für Argumente verwenden, und **wenn Sie sich unsicher sind, lassen Sie die Argumenttypen weg**. Sie können immer später Argumenttyp-Spezifikationen hinzufügen, wenn sie notwendig werden, und Sie opfern keine Leistung oder Funktionalität, indem Sie sie weglassen.

## The `return` Keyword

Der von einer Funktion zurückgegebene Wert ist der Wert des letzten ausgewerteten Ausdrucks, der standardmäßig der letzte Ausdruck im Körper der Funktionsdefinition ist. In der Beispiel-Funktion `f` aus dem vorherigen Abschnitt ist dies der Wert des Ausdrucks `x + y`. Alternativ, wie in vielen anderen Sprachen, bewirkt das Schlüsselwort `return`, dass eine Funktion sofort zurückgibt und einen Ausdruck bereitstellt, dessen Wert zurückgegeben wird:

```julia
function g(x, y)
    return x * y
    x + y
end
```

Da Funktionsdefinitionen in interaktive Sitzungen eingegeben werden können, ist es einfach, diese Definitionen zu vergleichen:

```jldoctest
julia> f(x, y) = x + y
f (generic function with 1 method)

julia> function g(x, y)
           return x * y
           x + y
       end
g (generic function with 1 method)

julia> f(2, 3)
5

julia> g(2, 3)
6
```

Natürlich ist die Verwendung von `return` in einem rein linearen Funktionskörper wie `g` sinnlos, da der Ausdruck `x + y` niemals ausgewertet wird und wir einfach `x * y` als letzten Ausdruck in der Funktion machen und das `return` weglassen könnten. In Verbindung mit anderen Kontrollflüssen ist `return` jedoch von echtem Nutzen. Hier ist zum Beispiel eine Funktion, die die Hypotenusenlänge eines rechtwinkligen Dreiecks mit Seitenlängen von `x` und `y` berechnet und Überläufe vermeidet:

```jldoctest
julia> function hypot(x, y)
           x = abs(x)
           y = abs(y)
           if x > y
               r = y/x
               return x*sqrt(1 + r*r)
           end
           if y == 0
               return zero(x)
           end
           r = x/y
           return y*sqrt(1 + r*r)
       end
hypot (generic function with 1 method)

julia> hypot(3, 4)
5.0
```

Es gibt drei mögliche Rückgabepunkte aus dieser Funktion, die die Werte von drei verschiedenen Ausdrücken zurückgeben, abhängig von den Werten von `x` und `y`. Das `return` in der letzten Zeile könnte weggelassen werden, da es der letzte Ausdruck ist.

### [Return type](@id man-functions-return-type)

Ein Rückgabewerttyp kann in der Funktionsdeklaration mit dem `::`-Operator angegeben werden. Dies konvertiert den Rückgabewert in den angegebenen Typ.

```jldoctest
julia> function g(x, y)::Int8
           return x * y
       end;

julia> typeof(g(1, 2))
Int8
```

Diese Funktion gibt immer ein `Int8` zurück, unabhängig von den Typen von `x` und `y`. Siehe [Type Declarations](@ref) für weitere Informationen zu Rückgabetypen.

Rückgabetypdeklarationen werden **selten verwendet** in Julia: Im Allgemeinen sollten Sie stattdessen "typstabile" Funktionen schreiben, bei denen der Compiler von Julia den Rückgabetyp automatisch ableiten kann. Für weitere Informationen siehe das Kapitel [Performance Tips](@ref man-performance-tips).

### Returning nothing

Für Funktionen, die keinen Wert zurückgeben müssen (Funktionen, die nur für einige Nebeneffekte verwendet werden), ist die Julia-Konvention, den Wert [`nothing`](@ref) zurückzugeben:

```julia
function printx(x)
    println("x = $x")
    return nothing
end
```

Dies ist eine *Konvention* im Sinne davon, dass `nothing` kein Julia-Schlüsselwort ist, sondern nur ein Singleton-Objekt vom Typ `Nothing`. Außerdem werden Sie vielleicht bemerken, dass das obige Beispiel der `printx`-Funktion konstruiert ist, da `println` bereits `nothing` zurückgibt, sodass die `return`-Zeile überflüssig ist.

Es gibt zwei mögliche verkürzte Formen für den Ausdruck `return nothing`. Einerseits gibt das Schlüsselwort `return` implizit `nothing` zurück, sodass es allein verwendet werden kann. Andererseits, da Funktionen implizit ihren letzten ausgewerteten Ausdruck zurückgeben, kann `nothing` allein verwendet werden, wenn es der letzte Ausdruck ist. Die Vorliebe für den Ausdruck `return nothing` im Gegensatz zu `return` oder `nothing` allein ist eine Frage des Programmierstils.

## Operators Are Functions

In Julia sind die meisten Operatoren einfach Funktionen mit Unterstützung für spezielle Syntax. (Die Ausnahmen sind Operatoren mit speziellen Auswertungssemantiken wie `&&` und `||`. Diese Operatoren können keine Funktionen sein, da [Short-Circuit Evaluation](@ref) erfordert, dass ihre Operanden nicht vor der Auswertung des Operators ausgewertet werden.) Dementsprechend können Sie sie auch mit geklammerten Argumentlisten anwenden, genau wie Sie es mit jeder anderen Funktion tun würden:

```jldoctest
julia> 1 + 2 + 3
6

julia> +(1, 2, 3)
6
```

Die Infix-Form ist genau äquivalent zur Funktionsanwendungsform – tatsächlich wird die erstere intern geparst, um den Funktionsaufruf zu erzeugen. Das bedeutet auch, dass Sie Operatoren wie [`+`](@ref) und [`*`](@ref) zuweisen und weitergeben können, genau wie Sie es mit anderen Funktionswerten tun würden:

```jldoctest
julia> f = +;

julia> f(1, 2, 3)
6
```

Unter dem Namen `f` unterstützt die Funktion jedoch keine Infix-Notation.

## Operators With Special Names

Einige spezielle Ausdrücke entsprechen Aufrufen von Funktionen mit nicht offensichtlichen Namen. Diese sind:

| Expression            | Calls                                    |
|:--------------------- |:---------------------------------------- |
| `[A B C ...]`         | [`hcat`](@ref)                           |
| `[A; B; C; ...]`      | [`vcat`](@ref)                           |
| `[A B; C D; ...]`     | [`hvcat`](@ref)                          |
| `[A; B;; C; D;; ...]` | [`hvncat`](@ref)                         |
| `A'`                  | [`adjoint`](@ref)                        |
| `A[i]`                | [`getindex`](@ref)                       |
| `A[i] = x`            | [`setindex!`](@ref)                      |
| `A.n`                 | [`getproperty`](@ref Base.getproperty)   |
| `A.n = x`             | [`setproperty!`](@ref Base.setproperty!) |

Beachten Sie, dass Ausdrücke, die ähnlich wie `[A; B;; C; D;; ...]` sind, aber mehr als zwei aufeinanderfolgende `;` enthalten, ebenfalls `hvncat`-Aufrufe entsprechen.

## [Anonymous Functions](@id man-anonymous-functions)

Funktionen in Julia sind [first-class objects](https://en.wikipedia.org/wiki/First-class_citizen): sie können Variablen zugewiesen und mit der standardmäßigen Funktionsaufrufsyntax von der Variablen, der sie zugewiesen wurden, aufgerufen werden. Sie können als Argumente verwendet und als Werte zurückgegeben werden. Sie können auch anonym erstellt werden, ohne einen Namen zu erhalten, indem eine dieser Syntaxen verwendet wird:

```jldoctest
julia> x -> x^2 + 2x - 1
#1 (generic function with 1 method)

julia> function (x)
           x^2 + 2x - 1
       end
#3 (generic function with 1 method)
```

Jede Anweisung erstellt eine Funktion, die ein Argument `x` entgegennimmt und den Wert des Polynoms `x^2 + 2x - 1` an diesem Wert zurückgibt. Beachten Sie, dass das Ergebnis eine generische Funktion ist, jedoch mit einem vom Compiler generierten Namen, der auf aufeinanderfolgender Nummerierung basiert.

Der Hauptzweck von anonymen Funktionen besteht darin, sie an Funktionen zu übergeben, die andere Funktionen als Argumente akzeptieren. Ein klassisches Beispiel ist [`map`](@ref), das eine Funktion auf jeden Wert eines Arrays anwendet und ein neues Array mit den resultierenden Werten zurückgibt:

```jldoctest
julia> map(round, [1.2, 3.5, 1.7])
3-element Vector{Float64}:
 1.0
 4.0
 2.0
```

Dies ist in Ordnung, wenn eine benannte Funktion, die die Transformation ausführt, bereits existiert, um sie als erstes Argument an [`map`](@ref) zu übergeben. Oft existiert jedoch keine einsatzbereite, benannte Funktion. In diesen Situationen ermöglicht der anonyme Funktionskonstruktor die einfache Erstellung eines einmal verwendbaren Funktionsobjekts, ohne einen Namen zu benötigen:

```jldoctest
julia> map(x -> x^2 + 2x - 1, [1, 3, -1])
3-element Vector{Int64}:
  2
 14
 -2
```

Eine anonyme Funktion, die mehrere Argumente akzeptiert, kann mit der Syntax `(x,y,z)->2x+y-z` geschrieben werden.

Argumenttyp-Deklarationen für anonyme Funktionen funktionieren wie bei benannten Funktionen, zum Beispiel `x::Integer->2x`. Der Rückgabetyp einer anonymen Funktion kann nicht angegeben werden.

Eine anonyme Funktion ohne Argumente kann als `()->2+2` geschrieben werden. Die Idee einer Funktion ohne Argumente mag seltsam erscheinen, ist jedoch in Fällen nützlich, in denen ein Ergebnis nicht (oder nicht vorab) berechnet werden kann. Zum Beispiel hat Julia eine null-Argumente [`time`](@ref) Funktion, die die aktuelle Zeit in Sekunden zurückgibt, und somit ist `seconds = ()->round(Int, time())` eine anonyme Funktion, die diese Zeit auf die nächste ganze Zahl gerundet zurückgibt und der Variablen `seconds` zugewiesen wird. Jedes Mal, wenn diese anonyme Funktion als `seconds()` aufgerufen wird, wird die aktuelle Zeit berechnet und zurückgegeben.

## Tuples

Julia hat eine eingebaute Datenstruktur namens *Tuple*, die eng mit Funktionsargumenten und Rückgabewerten verbunden ist. Ein Tuple ist ein Container fester Länge, der beliebige Werte halten kann, aber nicht modifiziert werden kann (es ist *unveränderlich*). Tuples werden mit Kommas und Klammern konstruiert und können über Indizes zugegriffen werden:

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"
```

Beachten Sie, dass ein Tupel der Länge 1 mit einem Komma geschrieben werden muss, `(1,)`, da `(1)` nur einen in Klammern gesetzten Wert darstellen würde. `()` steht für das leere (Länge-0) Tupel.

## Named Tuples

Die Komponenten von Tupeln können optional benannt werden, in diesem Fall wird ein *benanntes Tupel* erstellt:

```jldoctest
julia> x = (a=2, b=1+2)
(a = 2, b = 3)

julia> x[1]
2

julia> x.a
2
```

Die Felder von benannten Tupeln können zusätzlich zur regulären Indizierungssyntax (`x[1]` oder `x[:a]`) auch durch Namen mit der Punkt-Syntax (`x.a`) zugegriffen werden.

## [Destructuring Assignment and Multiple Return Values](@id destructuring-assignment)

Eine durch Kommas getrennte Liste von Variablen (optional in Klammern eingeschlossen) kann auf der linken Seite einer Zuweisung erscheinen: Der Wert auf der rechten Seite wird *destrukturiert*, indem über ihn iteriert und nacheinander jeder Variablen zugewiesen wird:

```jldoctest
julia> (a, b, c) = 1:3
1:3

julia> b
2
```

Der Wert auf der rechten Seite sollte ein Iterator sein (siehe [Iteration interface](@ref man-interface-iteration)), der mindestens so lang ist wie die Anzahl der Variablen auf der linken Seite (alle überschüssigen Elemente des Iterators werden ignoriert).

Dies kann verwendet werden, um mehrere Werte aus Funktionen zurückzugeben, indem ein Tupel oder ein anderes iterierbares Wert zurückgegeben wird. Zum Beispiel gibt die folgende Funktion zwei Werte zurück:

```jldoctest foofunc
julia> function foo(a, b)
           a+b, a*b
       end
foo (generic function with 1 method)
```

Wenn Sie es in einer interaktiven Sitzung aufrufen, ohne den Rückgabewert irgendwo zuzuweisen, sehen Sie das zurückgegebene Tupel:

```jldoctest foofunc
julia> foo(2, 3)
(5, 6)
```

Die Destrukturierungszuweisung extrahiert jeden Wert in eine Variable:

```jldoctest foofunc
julia> x, y = foo(2, 3)
(5, 6)

julia> x
5

julia> y
6
```

Ein weiterer häufiger Gebrauch ist das Tauschen von Variablen:

```jldoctest foofunc
julia> y, x = x, y
(5, 6)

julia> x
6

julia> y
5
```

Wenn nur eine Teilmenge der Elemente des Iterators benötigt wird, ist es eine gängige Konvention, ignorierte Elemente einer Variablen zuzuweisen, die nur aus Unterstrichen `_` besteht (was ein ansonsten ungültiger Variablenname ist, siehe [Allowed Variable Names](@ref man-allowed-variable-names)):

```jldoctest
julia> _, _, _, d = 1:10
1:10

julia> d
4
```

Andere gültige linke Seiten-Ausdrücke können als Elemente der Zuweisungsliste verwendet werden, die [`setindex!`](@ref) oder [`setproperty!`](@ref) aufrufen oder rekursiv einzelne Elemente des Iterators destrukturieren:

```jldoctest
julia> X = zeros(3);

julia> X[1], (a, b) = (1, (2, 3))
(1, (2, 3))

julia> X
3-element Vector{Float64}:
 1.0
 0.0
 0.0

julia> a
2

julia> b
3
```

!!! compat "Julia 1.6"
    `...` mit Zuweisung erfordert Julia 1.6


Wenn das letzte Symbol in der Zuweisungsliste mit `...` (bekannt als *slurping*) versehen ist, wird es einer Sammlung oder einem faulen Iterator der verbleibenden Elemente des Iterators auf der rechten Seite zugewiesen:

```jldoctest
julia> a, b... = "hello"
"hello"

julia> a
'h': ASCII/Unicode U+0068 (category Ll: Letter, lowercase)

julia> b
"ello"

julia> a, b... = Iterators.map(abs2, 1:4)
Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4)

julia> a
1

julia> b
Base.Iterators.Rest{Base.Generator{UnitRange{Int64}, typeof(abs2)}, Int64}(Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4), 1)
```

Siehe [`Base.rest`](@ref) für Details zur genauen Handhabung und Anpassung spezifischer Iteratoren.

!!! compat "Julia 1.9"
    `...` in nicht-finaler Position einer Zuweisung erfordert Julia 1.9


Das Schlürfen in Aufgaben kann auch in jeder anderen Position auftreten. Im Gegensatz zum Schlürfen am Ende einer Sammlung wird dies jedoch immer eifrig sein.

```jldoctest
julia> a, b..., c = 1:5
1:5

julia> a
1

julia> b
3-element Vector{Int64}:
 2
 3
 4

julia> c
5

julia> front..., tail = "Hi!"
"Hi!"

julia> front
"Hi"

julia> tail
'!': ASCII/Unicode U+0021 (category Po: Punctuation, other)
```

Dies ist in Bezug auf die Funktion [`Base.split_rest`](@ref) implementiert.

Beachten Sie, dass beim Definieren von variadischen Funktionen das Slurping nur in der letzten Position erlaubt ist. Dies gilt jedoch nicht für [single argument destructuring](@ref man-argument-destructuring), da dies die Methodenaufrufverarbeitung nicht beeinflusst:

```jldoctest
julia> f(x..., y) = x
ERROR: syntax: invalid "..." on non-final argument
Stacktrace:
[...]

julia> f((x..., y)) = x
f (generic function with 1 method)

julia> f((1, 2, 3))
(1, 2)
```

## Property destructuring

Anstatt die Destrukturierung basierend auf der Iteration durchzuführen, können auch die rechten Seiten von Zuweisungen mithilfe von Eigenschaftsnamen destrukturiert werden. Dies folgt der Syntax für NamedTuples und funktioniert, indem jeder Variable auf der linken Seite eine Eigenschaft der rechten Seite der Zuweisung mit demselben Namen unter Verwendung von `getproperty` zugewiesen wird:

```jldoctest
julia> (; b, a) = (a=1, b=2, c=3)
(a = 1, b = 2, c = 3)

julia> a
1

julia> b
2
```

## [Argument destructuring](@id man-argument-destructuring)

Die Destrukturierungsfunktion kann auch innerhalb eines Funktionsarguments verwendet werden. Wenn der Name eines Funktionsarguments als Tupel (z. B. `(x, y)`) anstelle nur eines Symbols geschrieben wird, wird eine Zuweisung `(x, y) = argument` für Sie eingefügt:

```julia-repl
julia> minmax(x, y) = (y < x) ? (y, x) : (x, y)

julia> gap((min, max)) = max - min

julia> gap(minmax(10, 2))
8
```

Beachten Sie die zusätzliche Klammer in der Definition von `gap`. Ohne diese wäre `gap` eine Funktion mit zwei Argumenten, und dieses Beispiel würde nicht funktionieren.

Ähnlich kann die Destrukturierung von Eigenschaften auch für Funktionsargumente verwendet werden:

```julia-repl
julia> foo((; x, y)) = x + y
foo (generic function with 1 method)

julia> foo((x=1, y=2))
3

julia> struct A
           x
           y
       end

julia> foo(A(3, 4))
7
```

Für anonyme Funktionen erfordert das Destrukturieren eines einzelnen Arguments ein zusätzliches Komma:

```
julia> map(((x, y),) -> x + y, [(1, 2), (3, 4)])
2-element Array{Int64,1}:
 3
 7
```

## Varargs Functions

Es ist oft praktisch, Funktionen zu schreiben, die eine beliebige Anzahl von Argumenten akzeptieren. Solche Funktionen sind traditionell als "varargs" Funktionen bekannt, was eine Abkürzung für "variable Anzahl von Argumenten" ist. Sie können eine varargs-Funktion definieren, indem Sie dem letzten Positionsargument drei Punkte folgen lassen:

```jldoctest barfunc
julia> bar(a, b, x...) = (a, b, x)
bar (generic function with 1 method)
```

Die Variablen `a` und `b` sind wie gewohnt an die ersten beiden Argumentwerte gebunden, und die Variable `x` ist an eine iterable Sammlung der null oder mehr Werte gebunden, die an `bar` nach seinen ersten beiden Argumenten übergeben werden:

```jldoctest barfunc
julia> bar(1, 2)
(1, 2, ())

julia> bar(1, 2, 3)
(1, 2, (3,))

julia> bar(1, 2, 3, 4)
(1, 2, (3, 4))

julia> bar(1, 2, 3, 4, 5, 6)
(1, 2, (3, 4, 5, 6))
```

In all diesen Fällen ist `x` an ein Tupel der übergebenen Nachfolgewerten an `bar` gebunden.

Es ist möglich, die Anzahl der Werte, die als variable Argumente übergeben werden, einzuschränken; dies wird später in [Parametrically-constrained Varargs methods](@ref) besprochen.

Auf der anderen Seite ist es oft praktisch, die Werte, die in einer iterierbaren Sammlung enthalten sind, in einen Funktionsaufruf als einzelne Argumente "auszupacken". Dazu verwendet man ebenfalls `...`, jedoch im Funktionsaufruf:

```jldoctest barfunc
julia> x = (3, 4)
(3, 4)

julia> bar(1, 2, x...)
(1, 2, (3, 4))
```

In diesem Fall wird ein Tupel von Werten genau dort in einen Varargs-Aufruf eingefügt, wo die variable Anzahl von Argumenten benötigt wird. Dies muss jedoch nicht der Fall sein:

```jldoctest barfunc
julia> x = (2, 3, 4)
(2, 3, 4)

julia> bar(1, x...)
(1, 2, (3, 4))

julia> x = (1, 2, 3, 4)
(1, 2, 3, 4)

julia> bar(x...)
(1, 2, (3, 4))
```

Darüber hinaus muss das iterable Objekt, das in einen Funktionsaufruf gesplittet wird, kein Tupel sein:

```jldoctest barfunc
julia> x = [3, 4]
2-element Vector{Int64}:
 3
 4

julia> bar(1, 2, x...)
(1, 2, (3, 4))

julia> x = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> bar(x...)
(1, 2, (3, 4))
```

Außerdem muss die Funktion, in die die Argumente gesplittet werden, keine Varargs-Funktion sein (obwohl sie es oft ist):

```jldoctest
julia> baz(a, b) = a + b;

julia> args = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> baz(args...)
3

julia> args = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> baz(args...)
ERROR: MethodError: no method matching baz(::Int64, ::Int64, ::Int64)
The function `baz` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  baz(::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

Wie Sie sehen können, schlägt der Funktionsaufruf fehl, wenn die falsche Anzahl von Elementen im gesplitteten Container vorhanden ist, genau wie es der Fall wäre, wenn zu viele Argumente explizit übergeben werden.

## Optional Arguments

Es ist oft möglich, sinnvolle Standardwerte für Funktionsargumente bereitzustellen. Dies kann den Benutzern helfen, nicht jedes Argument bei jedem Aufruf übergeben zu müssen. Zum Beispiel konstruiert die Funktion [`Date(y, [m, d])`](@ref) aus dem `Dates`-Modul einen `Date`-Typ für ein gegebenes Jahr `y`, Monat `m` und Tag `d`. Die Argumente `m` und `d` sind jedoch optional und ihr Standardwert ist `1`. Dieses Verhalten kann prägnant ausgedrückt werden als:

```jldoctest date_default_args
julia> using Dates

julia> function date(y::Int64, m::Int64=1, d::Int64=1)
           err = Dates.validargs(Date, y, m, d)
           err === nothing || throw(err)
           return Date(Dates.UTD(Dates.totaldays(y, m, d)))
       end
date (generic function with 3 methods)
```

Beachten Sie, dass diese Definition eine andere Methode der `Date`-Funktion aufruft, die ein Argument vom Typ `UTInstant{Day}` entgegennimmt.

Mit dieser Definition kann die Funktion mit entweder einem, zwei oder drei Argumenten aufgerufen werden, und `1` wird automatisch übergeben, wenn nur eines oder zwei der Argumente angegeben sind:

```jldoctest date_default_args
julia> date(2000, 12, 12)
2000-12-12

julia> date(2000, 12)
2000-12-01

julia> date(2000)
2000-01-01
```

Optionale Argumente sind eigentlich nur eine praktische Syntax, um mehrere Methodendefinitionen mit unterschiedlichen Argumentanzahlen zu schreiben (siehe [Note on Optional and keyword Arguments](@ref)). Dies kann für unser Beispiel der `date`-Funktion überprüft werden, indem die `methods`-Funktion aufgerufen wird:

```julia-repl
julia> methods(date)
# 3 methods for generic function "date":
[1] date(y::Int64) in Main at REPL[1]:1
[2] date(y::Int64, m::Int64) in Main at REPL[1]:1
[3] date(y::Int64, m::Int64, d::Int64) in Main at REPL[1]:1
```

## Keyword Arguments

Einige Funktionen benötigen eine große Anzahl von Argumenten oder haben eine große Anzahl von Verhaltensweisen. Sich daran zu erinnern, wie man solche Funktionen aufruft, kann schwierig sein. Schlüsselwortargumente können diese komplexen Schnittstellen einfacher zu verwenden und zu erweitern machen, indem sie es ermöglichen, Argumente nach Namen anstelle von nur nach Position zu identifizieren.

Zum Beispiel, betrachten Sie eine Funktion `plot`, die eine Linie zeichnet. Diese Funktion könnte viele Optionen haben, um den Linienstil, die Breite, die Farbe usw. zu steuern. Wenn sie Schlüsselwortargumente akzeptiert, könnte ein möglicher Aufruf so aussehen: `plot(x, y, width=2)`, wobei wir uns entschieden haben, nur die Linienbreite anzugeben. Beachten Sie, dass dies zwei Zwecke erfüllt. Der Aufruf ist leichter zu lesen, da wir ein Argument mit seiner Bedeutung kennzeichnen können. Es wird auch möglich, eine beliebige Teilmenge einer großen Anzahl von Argumenten in beliebiger Reihenfolge zu übergeben.

Funktionen mit Schlüsselwortargumenten werden in der Signatur mit einem Semikolon definiert:

```julia
function plot(x, y; style="solid", width=1, color="black")
    ###
end
```

Wenn die Funktion aufgerufen wird, ist das Semikolon optional: Man kann entweder `plot(x, y, width=2)` oder `plot(x, y; width=2)` aufrufen, aber der erstgenannte Stil ist gebräuchlicher. Ein explizites Semikolon ist nur erforderlich, um varargs oder berechnete Schlüsselwörter wie unten beschrieben zu übergeben.

Keyword-Argument-Standardwerte werden nur bei Bedarf ausgewertet (wenn ein entsprechendes Schlüsselwort-Argument nicht übergeben wird) und in der Reihenfolge von links nach rechts. Daher können Standardausdrücke auf vorherige Schlüsselwort-Argumente verweisen.

Die Arten von Schlüsselwortargumenten können wie folgt explizit gemacht werden:

```julia
function f(; x::Int=1)
    ###
end
```

Schlüsselwortargumente können auch in Varargs-Funktionen verwendet werden:

```julia
function plot(x...; style="solid")
    ###
end
```

Zusätzliche Schlüsselwortargumente können mit `...` gesammelt werden, wie in varargs-Funktionen:

```julia
function f(x; y=0, kwargs...)
    ###
end
```

Innerhalb von `f` wird `kwargs` ein unveränderlicher Schlüssel-Wert-Iterator über ein benanntes Tupel sein. Benannte Tupel (sowie Wörterbücher mit Schlüsseln vom Typ `Symbol` und andere Iteratoren, die zweiwertige Sammlungen mit Symbolen als ersten Werten erzeugen) können als Schlüsselwörter mit einem Semikolon in einem Aufruf übergeben werden, z. B. `f(x, z=1; kwargs...)`.

Wenn ein Schlüsselwortargument in der Methodendefinition keinen Standardwert zugewiesen bekommt, ist es *erforderlich*: eine [`UndefKeywordError`](@ref) Ausnahme wird ausgelöst, wenn der Aufrufer ihm keinen Wert zuweist:

```julia
function f(x; y)
    ###
end
f(3, y=5) # ok, y is assigned
f(3)      # throws UndefKeywordError(:y)
```

Man kann auch `key => value`-Ausdrücke nach einem Semikolon übergeben. Zum Beispiel ist `plot(x, y; :width => 2)` äquivalent zu `plot(x, y, width=2)`. Dies ist nützlich in Situationen, in denen der Schlüsselname zur Laufzeit berechnet wird.

Wenn ein nackter Bezeichner oder ein Punktausdruck nach einem Semikolon auftritt, wird der Schlüsselwort-Argumentname durch den Bezeichner oder den Feldnamen impliziert. Zum Beispiel ist `plot(x, y; width)` äquivalent zu `plot(x, y; width=width)` und `plot(x, y; options.width)` ist äquivalent zu `plot(x, y; width=options.width)`.

Die Natur der Schlüsselwortargumente macht es möglich, dass dasselbe Argument mehr als einmal angegeben werden kann. Zum Beispiel ist es im Aufruf `plot(x, y; options..., width=2)` möglich, dass die `options`-Struktur auch einen Wert für `width` enthält. In einem solchen Fall hat das rechtsstehende Vorkommen Vorrang; in diesem Beispiel wird `width` mit Sicherheit den Wert `2` haben. Das mehrfache explizite Angeben desselben Schlüsselwortarguments, zum Beispiel `plot(x, y, width=2, width=3)`, ist jedoch nicht erlaubt und führt zu einem Syntaxfehler.

## Evaluation Scope of Default Values

Wenn optionale und Schlüsselwortargument-Standardausdrücke ausgewertet werden, sind nur *vorherige* Argumente im Geltungsbereich. Zum Beispiel, gegeben diese Definition:

```julia
function f(x, a=b, b=1)
    ###
end
```

das `b` in `a=b` bezieht sich auf ein `b` in einem äußeren Gültigkeitsbereich, nicht auf das nachfolgende Argument `b`.

## Do-Block Syntax for Function Arguments

Das Übergeben von Funktionen als Argumente an andere Funktionen ist eine leistungsstarke Technik, aber die Syntax dafür ist nicht immer bequem. Solche Aufrufe sind besonders umständlich zu schreiben, wenn das Funktionsargument mehrere Zeilen erfordert. Als Beispiel betrachten wir den Aufruf [`map`](@ref) bei einer Funktion mit mehreren Fällen:

```julia
map(x->begin
           if x < 0 && iseven(x)
               return 0
           elseif x == 0
               return 1
           else
               return x
           end
       end,
    [A, B, C])
```

Julia bietet ein reserviertes Wort `do`, um diesen Code klarer umzuschreiben:

```julia
map([A, B, C]) do x
    if x < 0 && iseven(x)
        return 0
    elseif x == 0
        return 1
    else
        return x
    end
end
```

Die `do x` Syntax erstellt eine anonyme Funktion mit dem Argument `x` und übergibt die anonyme Funktion als erstes Argument an die "äußere" Funktion - [`map`](@ref) in diesem Beispiel. Ebenso würde `do a,b` eine anonyme Funktion mit zwei Argumenten erstellen. Beachten Sie, dass `do (a,b)` eine anonyme Funktion mit einem Argument erstellen würde, dessen Argument ein Tupel ist, das dekonstruierbar ist. Ein einfaches `do` würde erklären, dass das, was folgt, eine anonyme Funktion der Form `() -> ...` ist.

Wie diese Argumente initialisiert werden, hängt von der "äußeren" Funktion ab; hier wird [`map`](@ref) nacheinander `x` auf `A`, `B`, `C` setzen und die anonyme Funktion bei jedem Aufruf aufrufen, genau wie es in der Syntax `map(func, [A, B, C])` der Fall wäre.

Diese Syntax erleichtert die Verwendung von Funktionen, um die Sprache effektiv zu erweitern, da Aufrufe wie normale Codeblöcke aussehen. Es gibt viele mögliche Anwendungen, die sich stark von [`map`](@ref) unterscheiden, wie z. B. das Verwalten des Systemzustands. Zum Beispiel gibt es eine Version von [`open`](@ref), die Code ausführt, der sicherstellt, dass die geöffnete Datei schließlich geschlossen wird:

```julia
open("outfile", "w") do io
    write(io, data)
end
```

Dies wird durch die folgende Definition erreicht:

```julia
function open(f::Function, args...)
    io = open(args...)
    try
        f(io)
    finally
        close(io)
    end
end
```

Hier öffnet [`open`](@ref) die Datei zum Schreiben und übergibt dann den resultierenden Ausgabestrom an die anonyme Funktion, die du im `do ... end`-Block definiert hast. Nachdem deine Funktion beendet ist, wird `4d61726b646f776e2e436f64652822222c20226f70656e2229_40726566` sicherstellen, dass der Strom ordnungsgemäß geschlossen wird, unabhängig davon, ob deine Funktion normal beendet wurde oder eine Ausnahme ausgelöst hat. (Der `try/finally`-Konstruktion wird in [Control Flow](@ref) beschrieben.)

Mit der `do`-Blocksyntax ist es hilfreich, die Dokumentation oder Implementierung zu überprüfen, um zu wissen, wie die Argumente der Benutzerfunktion initialisiert werden.

Ein `do`-Block kann, wie jede andere innere Funktion, Variablen aus seinem umgebenden Geltungsbereich "erfassen". Zum Beispiel wird die Variable `data` im obigen Beispiel von `open...do` aus dem äußeren Geltungsbereich erfasst. Erfasste Variablen können, wie in [performance tips](@ref man-performance-captured) besprochen, Leistungsprobleme verursachen.

## Function composition and piping

Funktionen in Julia können durch Komposition oder Piping (Verkettung) miteinander kombiniert werden.

Die Funktionskomposition ist, wenn Sie Funktionen zusammen kombinieren und die resultierende Komposition auf Argumente anwenden. Sie verwenden den Funktionskompositionsoperator (`∘`), um die Funktionen zu komponieren, sodass `(f ∘ g)(args...; kw...)` dasselbe ist wie `f(g(args...; kw...))`.

Sie können den Kompositionsoperator an der REPL und in entsprechend konfigurierten Editoren mit `\circ<tab>` eingeben.

Zum Beispiel können die Funktionen `sqrt` und `+` wie folgt kombiniert werden:

```jldoctest
julia> (sqrt ∘ +)(3, 6)
3.0
```

Dies addiert zuerst die Zahlen und findet dann die Quadratwurzel des Ergebnisses.

Das nächste Beispiel setzt drei Funktionen zusammen und wendet das Ergebnis auf ein Array von Strings an:

```jldoctest
julia> map(first ∘ reverse ∘ uppercase, split("you can compose functions like this"))
6-element Vector{Char}:
 'U': ASCII/Unicode U+0055 (category Lu: Letter, uppercase)
 'N': ASCII/Unicode U+004E (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
```

Funktionenkettung (manchmal als "Piping" oder "eine Pipe verwenden" bezeichnet, um Daten an eine nachfolgende Funktion zu senden) ist, wenn Sie eine Funktion auf die Ausgabe der vorherigen Funktion anwenden:

```jldoctest
julia> 1:10 |> sum |> sqrt
7.416198487095663
```

Hier wird die Gesamtsumme von `sum` an die Funktion `sqrt` übergeben. Die äquivalente Zusammensetzung wäre:

```jldoctest
julia> (sqrt ∘ sum)(1:10)
7.416198487095663
```

Der Pipe-Operator kann auch mit Broadcasting verwendet werden, als `.|>`, um eine nützliche Kombination der Verkettungs-/Pipe- und Punktvektorisierungs-Syntax bereitzustellen (siehe unten).

```jldoctest
julia> ["a", "list", "of", "strings"] .|> [uppercase, reverse, titlecase, length]
4-element Vector{Any}:
  "A"
  "tsil"
  "Of"
 7
```

Wenn Sie Pipes mit anonymen Funktionen kombinieren, müssen Klammern verwendet werden, wenn nachfolgende Pipes nicht als Teil des Körpers der anonymen Funktion interpretiert werden sollen. Vergleichen Sie:

```jldoctest
julia> 1:3 .|> (x -> x^2) |> sum |> sqrt
3.7416573867739413

julia> 1:3 .|> x -> x^2 |> sum |> sqrt
3-element Vector{Float64}:
 1.0
 2.0
 3.0
```

## [Dot Syntax for Vectorizing Functions](@id man-vectorized)

In technischen Programmiersprachen ist es üblich, "vektorisierte" Versionen von Funktionen zu haben, die einfach eine gegebene Funktion `f(x)` auf jedes Element eines Arrays `A` anwenden, um ein neues Array über `f(A)` zu erzeugen. Diese Art von Syntax ist praktisch für die Datenverarbeitung, aber in anderen Sprachen ist Vektorisierung auch oft für die Leistung erforderlich: Wenn Schleifen langsam sind, kann die "vektorisierte" Version einer Funktion schnellen Bibliothekscode aufrufen, der in einer niedrigeren Programmiersprache geschrieben ist. In Julia sind vektorisierte Funktionen *nicht* für die Leistung erforderlich, und es ist in der Tat oft vorteilhaft, eigene Schleifen zu schreiben (siehe [Performance Tips](@ref man-performance-tips)), aber sie können dennoch praktisch sein. Daher kann *jede* Julia-Funktion `f` elementweise auf jedes Array (oder eine andere Sammlung) mit der Syntax `f.(A)` angewendet werden. Zum Beispiel kann `sin` auf alle Elemente im Vektor `A` wie folgt angewendet werden:

```jldoctest
julia> A = [1.0, 2.0, 3.0]
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> sin.(A)
3-element Vector{Float64}:
 0.8414709848078965
 0.9092974268256817
 0.1411200080598672
```

Natürlich können Sie den Punkt weglassen, wenn Sie eine spezialisierte "Vektor"-Methode von `f` schreiben, z. B. über `f(A::AbstractArray) = map(f, A)`, und dies ist ebenso effizient wie `f.(A)`. Der Vorteil der Syntax `f.(A)` besteht darin, dass nicht im Voraus entschieden werden muss, welche Funktionen vektorisierbar sind, von dem Bibliotheksautor.

Allgemeiner gesagt, `f.(args...)` ist tatsächlich äquivalent zu `broadcast(f, args...)`, was es Ihnen ermöglicht, auf mehrere Arrays (sogar unterschiedlicher Formen) oder eine Mischung aus Arrays und Skalaren zu operieren (siehe [Broadcasting](@ref)). Zum Beispiel, wenn Sie `f(x, y) = 3x + 4y` haben, dann wird `f.(pi, A)` ein neues Array zurückgeben, das aus `f(pi,a)` für jedes `a` in `A` besteht, und `f.(vector1, vector2)` wird einen neuen Vektor zurückgeben, der aus `f(vector1[i], vector2[i])` für jeden Index `i` besteht (und eine Ausnahme auslösen, wenn die Vektoren unterschiedliche Längen haben).

```jldoctest
julia> f(x, y) = 3x + 4y;

julia> A = [1.0, 2.0, 3.0];

julia> B = [4.0, 5.0, 6.0];

julia> f.(pi, A)
3-element Vector{Float64}:
 13.42477796076938
 17.42477796076938
 21.42477796076938

julia> f.(A, B)
3-element Vector{Float64}:
 19.0
 26.0
 33.0
```

Schlüsselwortargumente werden nicht übertragen, sondern einfach bei jedem Aufruf der Funktion weitergegeben. Zum Beispiel ist `round.(x, digits=3)` äquivalent zu `broadcast(x -> round(x, digits=3), x)`.

Darüber hinaus werden *verschachtelte* `f.(args...)`-Aufrufe in eine einzige `broadcast`-Schleife *fusioniert*. Zum Beispiel ist `sin.(cos.(X))` äquivalent zu `broadcast(x -> sin(cos(x)), X)`, ähnlich wie `[sin(cos(x)) for x in X]`: es gibt nur eine einzige Schleife über `X`, und ein einzelnes Array wird für das Ergebnis zugewiesen. [Im Gegensatz dazu würde `sin(cos(X))` in einer typischen "vektorisierten" Sprache zunächst ein temporäres Array für `tmp=cos(X)` zuweisen und dann `sin(tmp)` in einer separaten Schleife berechnen, wobei ein zweites Array zugewiesen wird.] Diese Schleifenfusion ist keine Compiler-Optimierung, die möglicherweise auftritt oder nicht, sondern eine *syntaktische Garantie*, wann immer verschachtelte `f.(args...)`-Aufrufe auftreten. Technisch stoppt die Fusion, sobald ein "Nicht-Punkt"-Funktionsaufruf auftritt; zum Beispiel können in `sin.(sort(cos.(X)))` die `sin`- und `cos`-Schleifen nicht zusammengeführt werden, aufgrund der dazwischenliegenden `sort`-Funktion.

Schließlich wird die maximale Effizienz typischerweise erreicht, wenn das Ausgabearray einer vektorisierten Operation *vorab zugewiesen* wird, sodass wiederholte Aufrufe nicht immer wieder neue Arrays für die Ergebnisse zuweisen (siehe [Pre-allocating outputs](@ref)). Eine praktische Syntax dafür ist `X .= ...`, was äquivalent zu `broadcast!(identity, X, ...)` ist, mit dem Unterschied, dass, wie oben erwähnt, die `broadcast!`-Schleife mit allen geschachtelten "Punkt"-Aufrufen fusioniert wird. Zum Beispiel ist `X .= sin.(Y)` äquivalent zu `broadcast!(sin, X, Y)`, wobei `X` in-place mit `sin.(Y)` überschrieben wird. Wenn die linke Seite ein Array-Indexausdruck ist, z. B. `X[begin+1:end] .= sin.(Y)`, dann wird dies zu `broadcast!` auf einem `view` übersetzt, z. B. `broadcast!(sin, view(X, firstindex(X)+1:lastindex(X)), Y)`, sodass die linke Seite in-place aktualisiert wird.

Da das Hinzufügen von Punkten zu vielen Operationen und Funktionsaufrufen in einem Ausdruck mühsam sein kann und zu schwer lesbarem Code führen kann, wird das Makro [`@.`](@ref @__dot__) bereitgestellt, um *jeden* Funktionsaufruf, jede Operation und jede Zuweisung in einem Ausdruck in die "punktierte" Version zu konvertieren.

```jldoctest
julia> Y = [1.0, 2.0, 3.0, 4.0];

julia> X = similar(Y); # pre-allocate output array

julia> @. X = sin(cos(Y)) # equivalent to X .= sin.(cos.(Y))
4-element Vector{Float64}:
  0.5143952585235492
 -0.4042391538522658
 -0.8360218615377305
 -0.6080830096407656
```

Binäre (oder unäre) Operatoren wie `.+` werden mit demselben Mechanismus behandelt: Sie sind äquivalent zu `broadcast`-Aufrufen und werden mit anderen geschachtelten "Punkt"-Aufrufen fusioniert. `X .+= Y` usw. ist äquivalent zu `X .= X .+ Y` und führt zu einer fusionierten In-Place-Zuweisung; siehe auch [dot operators](@ref man-dot-operators).

Sie können auch Punktoperationen mit Funktionsverkettung kombinieren, indem Sie [`|>`](@ref) verwenden, wie in diesem Beispiel:

```jldoctest
julia> 1:5 .|> [x->x^2, inv, x->2*x, -, isodd]
5-element Vector{Real}:
    1
    0.5
    6
   -4
 true
```

Alle Funktionen im fusionierten Broadcast werden immer für jedes Element des Ergebnisses aufgerufen. Daher wird `X .+ σ .* randn.()` eine Maske von unabhängig und identisch verteilten Zufallswerten zu jedem Element des Arrays `X` hinzufügen, während `X .+ σ .* randn()` die *gleichen* Zufallswerte zu jedem Element hinzufügen wird. In Fällen, in denen die fusionierte Berechnung entlang einer oder mehrerer Achsen der Broadcast-Iteration konstant ist, kann es möglich sein, einen Raum-Zeit-Handel zu nutzen und Zwischenwerte zuzuweisen, um die Anzahl der Berechnungen zu reduzieren. Weitere Informationen finden Sie unter [performance tips](@ref man-performance-unfuse).

## Further Reading

Wir sollten hier erwähnen, dass dies bei weitem kein vollständiges Bild der Funktionsdefinitionen ist. Julia hat ein ausgeklügeltes Typsystem und erlaubt Mehrfachdispatch auf Argumenttypen. Keines der hier gegebenen Beispiele enthält Typannotationen für ihre Argumente, was bedeutet, dass sie für alle Typen von Argumenten anwendbar sind. Das Typsystem wird in [Types](@ref man-types) beschrieben, und die Definition einer Funktion in Bezug auf Methoden, die durch Mehrfachdispatch auf Laufzeit-Argumenttypen ausgewählt werden, wird in [Methods](@ref) beschrieben.
