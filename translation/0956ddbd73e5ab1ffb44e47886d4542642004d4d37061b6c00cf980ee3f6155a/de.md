# Metaprogramming

Das stärkste Erbe von Lisp in der Julia-Sprache ist ihre Unterstützung für Metaprogrammierung. Wie Lisp stellt Julia ihren eigenen Code als Datenstruktur der Sprache selbst dar. Da Code durch Objekte repräsentiert wird, die innerhalb der Sprache erstellt und manipuliert werden können, ist es möglich, dass ein Programm seinen eigenen Code transformiert und generiert. Dies ermöglicht eine ausgeklügelte Code-Generierung ohne zusätzliche Build-Schritte und erlaubt auch echte Lisp-ähnliche Makros, die auf der Ebene von [abstract syntax trees](https://en.wikipedia.org/wiki/Abstract_syntax_tree) arbeiten. Im Gegensatz dazu führen Präprozessor-"Makro"-Systeme, wie das von C und C++, textuelle Manipulation und Substitution durch, bevor eine tatsächliche Analyse oder Interpretation erfolgt. Da alle Datentypen und Codes in Julia durch Julia-Datenstrukturen repräsentiert werden, sind leistungsstarke [reflection](https://en.wikipedia.org/wiki/Reflection_%28computer_programming%29) Fähigkeiten verfügbar, um die Interna eines Programms und seiner Typen wie jede andere Daten zu erkunden.

!!! warning
    Metaprogrammierung ist ein leistungsstarkes Werkzeug, aber sie führt zu Komplexität, die den Code schwieriger verständlich machen kann. Zum Beispiel kann es überraschend schwierig sein, die Geltungsregeln korrekt zu erfassen. Metaprogrammierung sollte typischerweise nur verwendet werden, wenn andere Ansätze wie [higher order functions](@ref man-anonymous-functions) und [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming)) nicht angewendet werden können.

    `eval` und das Definieren neuer Makros sollten typischerweise als letztes Mittel verwendet werden. Es ist fast nie eine gute Idee, `Meta.parse` zu verwenden oder einen beliebigen String in Julia-Code umzuwandeln. Um Julia-Code zu manipulieren, verwenden Sie direkt die `Expr`-Datenstruktur, um die Komplexität zu vermeiden, wie Julia-Syntax geparst wird.

    Die besten Anwendungen von Metaprogrammierung implementieren oft den Großteil ihrer Funktionalität in Laufzeit-Hilfsfunktionen und bemühen sich, die Menge des generierten Codes zu minimieren.


## Program representation

Jedes Julia-Programm beginnt sein Leben als eine Zeichenkette:

```jldoctest prog
julia> prog = "1 + 1"
"1 + 1"
```

**Was passiert als Nächstes?**

Der nächste Schritt besteht darin, [parse](https://en.wikipedia.org/wiki/Parsing#Computer_languages) jeden String in ein Objekt namens Ausdruck zu konvertieren, das durch den Julia-Typ [`Expr`](@ref) dargestellt wird:

```jldoctest prog
julia> ex1 = Meta.parse(prog)
:(1 + 1)

julia> typeof(ex1)
Expr
```

`Expr`-Objekte bestehen aus zwei Teilen:

  * ein [`Symbol`](@ref) identifiziert die Art des Ausdrucks. Ein Symbol ist ein [interned string](https://en.wikipedia.org/wiki/String_interning) Bezeichner (weitere Diskussion unten).

```jldoctest prog
julia> ex1.head
:call
```

  * die Ausdrucksargumente, die Symbole, andere Ausdrücke oder literale Werte sein können:

```jldoctest prog
julia> ex1.args
3-element Vector{Any}:
  :+
 1
 1
```

Ausdrücke können auch direkt in [prefix notation](https://en.wikipedia.org/wiki/Polish_notation) konstruiert werden:

```jldoctest prog
julia> ex2 = Expr(:call, :+, 1, 1)
:(1 + 1)
```

Die beiden oben konstruierten Ausdrücke – durch Parsen und durch direkte Konstruktion – sind äquivalent:

```jldoctest prog
julia> ex1 == ex2
true
```

**Der entscheidende Punkt hier ist, dass Julia-Code intern als eine Datenstruktur dargestellt wird, die von der Sprache selbst zugänglich ist.**

Die [`dump`](@ref)-Funktion bietet eine eingerückte und annotierte Anzeige von `Expr`-Objekten:

```jldoctest prog
julia> dump(ex2)
Expr
  head: Symbol call
  args: Array{Any}((3,))
    1: Symbol +
    2: Int64 1
    3: Int64 1
```

`Expr`-Objekte können auch geschachtelt sein:

```jldoctest ex3
julia> ex3 = Meta.parse("(4 + 4) / 2")
:((4 + 4) / 2)
```

Eine andere Möglichkeit, Ausdrücke anzuzeigen, ist mit `Meta.show_sexpr`, das die [S-expression](https://en.wikipedia.org/wiki/S-expression)-Form eines gegebenen `Expr` anzeigt, die Benutzern von Lisp sehr vertraut erscheinen mag. Hier ist ein Beispiel, das die Anzeige eines verschachtelten `Expr` veranschaulicht:

```jldoctest ex3
julia> Meta.show_sexpr(ex3)
(:call, :/, (:call, :+, 4, 4), 2)
```

### Symbols

Der `:`-Zeichen hat in Julia zwei syntaktische Zwecke. Die erste Form erstellt ein [`Symbol`](@ref), ein [interned string](https://en.wikipedia.org/wiki/String_interning), das als ein Baustein von Ausdrücken aus gültigen Bezeichnern verwendet wird:

```jldoctest
julia> s = :foo
:foo

julia> typeof(s)
Symbol
```

Der [`Symbol`](@ref) Konstruktor nimmt eine beliebige Anzahl von Argumenten und erstellt ein neues Symbol, indem er deren String-Darstellungen zusammenfügt:

```jldoctest
julia> :foo === Symbol("foo")
true

julia> Symbol("1foo") # `:1foo` would not work, as `1foo` is not a valid identifier
Symbol("1foo")

julia> Symbol("func",10)
:func10

julia> Symbol(:var,'_',"sym")
:var_sym
```

Im Kontext eines Ausdrucks werden Symbole verwendet, um den Zugriff auf Variablen anzuzeigen; wenn ein Ausdruck ausgewertet wird, wird ein Symbol durch den Wert ersetzt, der mit diesem Symbol in der entsprechenden [scope](@ref scope-of-variables) verknüpft ist.

Manchmal sind zusätzliche Klammern um das Argument zu `:` erforderlich, um Mehrdeutigkeiten beim Parsen zu vermeiden:

```jldoctest
julia> :(:)
:(:)

julia> :(::)
:(::)
```

## Expressions and evaluation

### Quoting

Der zweite syntaktische Zweck des `:`-Zeichens besteht darin, Ausdrucksobjekte zu erstellen, ohne den expliziten [`Expr`](@ref)-Konstruktor zu verwenden. Dies wird als *Zitat* bezeichnet. Das `:`-Zeichen, gefolgt von gepaarten Klammern um eine einzelne Anweisung von Julia-Code, erzeugt ein `Expr`-Objekt basierend auf dem eingeschlossenen Code. Hier ist ein Beispiel für die Kurzform, die verwendet wird, um einen arithmetischen Ausdruck zu zitieren:

```jldoctest
julia> ex = :(a+b*c+1)
:(a + b * c + 1)

julia> typeof(ex)
Expr
```

(zum Anzeigen der Struktur dieses Ausdrucks, versuchen Sie `ex.head` und `ex.args`, oder verwenden Sie [`dump`](@ref) wie oben oder [`Meta.@dump`](@ref))

Beachten Sie, dass äquivalente Ausdrücke unter Verwendung von [`Meta.parse`](@ref) oder der direkten `Expr`-Form erstellt werden können:

```jldoctest
julia>      :(a + b*c + 1)       ==
       Meta.parse("a + b*c + 1") ==
       Expr(:call, :+, :a, Expr(:call, :*, :b, :c), 1)
true
```

Ausdrücke, die vom Parser bereitgestellt werden, haben im Allgemeinen nur Symbole, andere Ausdrücke und literale Werte als ihre Argumente, während Ausdrücke, die durch Julia-Code konstruiert werden, beliebige Laufzeitwerte ohne literale Formen als Argumente haben können. In diesem speziellen Beispiel sind `+` und `a` Symbole, `*(b,c)` ist ein Unterausdruck, und `1` ist eine literale 64-Bit vorzeichenbehaftete Ganzzahl.

Es gibt eine zweite syntaktische Form des Zitierens für mehrere Ausdrücke: Codeblöcke, die in `quote ... end` eingeschlossen sind.

```jldoctest
julia> ex = quote
           x = 1
           y = 2
           x + y
       end
quote
    #= none:2 =#
    x = 1
    #= none:3 =#
    y = 2
    #= none:4 =#
    x + y
end

julia> typeof(ex)
Expr
```

### [Interpolation](@id man-expression-interpolation)

Die direkte Konstruktion von [`Expr`](@ref)-Objekten mit Wertargumenten ist mächtig, aber `Expr`-Konstruktoren können im Vergleich zur "normalen" Julia-Syntax mühsam sein. Als Alternative erlaubt Julia die *Interpolation* von Literalen oder Ausdrücken in zitierte Ausdrücke. Die Interpolation wird durch ein Präfix `$` angezeigt.

In diesem Beispiel wird der Wert der Variablen `a` interpoliert:

```jldoctest interp1
julia> a = 1;

julia> ex = :($a + b)
:(1 + b)
```

Die Interpolation in einen nicht zitierten Ausdruck wird nicht unterstützt und führt zu einem Kompilierungsfehler:

```jldoctest interp1
julia> $a + b
ERROR: syntax: "$" expression outside quote
```

In diesem Beispiel wird das Tupel `(1,2,3)` als Ausdruck in einen bedingten Test interpoliert:

```jldoctest interp1
julia> ex = :(a in $:((1,2,3)) )
:(a in (1, 2, 3))
```

Die Verwendung von `$` für die Ausdrucksinterpolation erinnert absichtlich an [string interpolation](@ref string-interpolation) und [command interpolation](@ref command-interpolation). Die Ausdrucksinterpolation ermöglicht eine bequeme, lesbare programmgesteuerte Konstruktion komplexer Julia-Ausdrücke.

### Splatting interpolation

Beachten Sie, dass die `$`-Interpolation-Syntax nur das Einfügen eines einzelnen Ausdrucks in einen umschließenden Ausdruck ermöglicht. Gelegentlich haben Sie ein Array von Ausdrücken und müssen alle zu Argumenten des umgebenden Ausdrucks machen. Dies kann mit der Syntax `$(xs...)` erreicht werden. Zum Beispiel erzeugt der folgende Code einen Funktionsaufruf, bei dem die Anzahl der Argumente programmgesteuert bestimmt wird:

```jldoctest interp1
julia> args = [:x, :y, :z];

julia> :(f(1, $(args...)))
:(f(1, x, y, z))
```

### Nested quote

Natürlich ist es möglich, dass Zitat-Ausdrücke andere Zitat-Ausdrücke enthalten. Das Verständnis, wie Interpolation in diesen Fällen funktioniert, kann etwas knifflig sein. Betrachten Sie dieses Beispiel:

```jldoctest interp1
julia> x = :(1 + 2);

julia> e = quote quote $x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :x))
end))
end
```

Beachten Sie, dass das Ergebnis `$x` enthält, was bedeutet, dass `x` noch nicht ausgewertet wurde. Mit anderen Worten, der `$`-Ausdruck "gehört" zum inneren Zitat-Ausdruck, und daher wird sein Argument nur ausgewertet, wenn der innere Zitat-Ausdruck ist:

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    1 + 2
end
```

Allerdings kann der äußere `quote`-Ausdruck Werte innerhalb des `$` im inneren Zitat interpolieren. Dies geschieht mit mehreren `$`s:

```jldoctest interp1
julia> e = quote quote $$x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :(1 + 2)))
end))
end
```

Beachten Sie, dass `(1 + 2)` jetzt im Ergebnis erscheint, anstelle des Symbols `x`. Die Auswertung dieses Ausdrucks ergibt ein interpoliertes `3`:

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    3
end
```

Die Intuition hinter diesem Verhalten ist, dass `x` für jedes `$` einmal ausgewertet wird: Ein `$` funktioniert ähnlich wie `eval(:x)`, was den Wert von `x` ergibt, während zwei `$` das Äquivalent von `eval(eval(:x))` darstellen.

### [QuoteNode](@id man-quote-node)

The usual representation of a `quote` form in an AST is an [`Expr`](@ref) with head `:quote`:

```jldoctest interp1
julia> dump(Meta.parse(":(1+2)"))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Expr
      head: Symbol call
      args: Array{Any}((3,))
        1: Symbol +
        2: Int64 1
        3: Int64 2
```

Wie wir gesehen haben, unterstützen solche Ausdrücke die Interpolation mit `$`. In einigen Situationen ist es jedoch notwendig, Code *ohne* Interpolation zu zitieren. Diese Art des Zitierens hat noch keine Syntax, wird jedoch intern als ein Objekt vom Typ `QuoteNode` dargestellt:

```jldoctest interp1
julia> eval(Meta.quot(Expr(:$, :(1+2))))
3

julia> eval(QuoteNode(Expr(:$, :(1+2))))
:($(Expr(:$, :(1 + 2))))
```

Der Parser erzeugt `QuoteNode`s für einfache zitierte Elemente wie Symbole:

```jldoctest interp1
julia> dump(Meta.parse(":x"))
QuoteNode
  value: Symbol x
```

`QuoteNode` kann auch für bestimmte fortgeschrittene Metaprogrammierungsaufgaben verwendet werden.

### Evaluating expressions

Gegeben ein Ausdrucksobjekt kann man Julia dazu bringen, es im globalen Kontext auszuführen, indem man [`eval`](@ref) verwendet:

```jldoctest interp1
julia> ex1 = :(1 + 2)
:(1 + 2)

julia> eval(ex1)
3

julia> ex = :(a + b)
:(a + b)

julia> eval(ex)
ERROR: UndefVarError: `b` not defined in `Main`
[...]

julia> a = 1; b = 2;

julia> eval(ex)
3
```

Jede [module](@ref modules) hat ihre eigene [`eval`](@ref) Funktion, die Ausdrücke in ihrem globalen Geltungsbereich auswertet. Ausdrücke, die an `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566` übergeben werden, sind nicht darauf beschränkt, Werte zurückzugeben – sie können auch Nebenwirkungen haben, die den Zustand der Umgebung des umschließenden Moduls verändern:

```jldoctest
julia> ex = :(x = 1)
:(x = 1)

julia> x
ERROR: UndefVarError: `x` not defined in `Main`

julia> eval(ex)
1

julia> x
1
```

Hier führt die Auswertung eines Ausdrucksobjekts dazu, dass ein Wert der globalen Variablen `x` zugewiesen wird.

Da Ausdrücke nur `Expr`-Objekte sind, die programmgesteuert erstellt und dann ausgewertet werden können, ist es möglich, beliebigen Code dynamisch zu generieren, der dann mit [`eval`](@ref) ausgeführt werden kann. Hier ist ein einfaches Beispiel:

```julia-repl
julia> a = 1;

julia> ex = Expr(:call, :+, a, :b)
:(1 + b)

julia> a = 0; b = 2;

julia> eval(ex)
3
```

Der Wert von `a` wird verwendet, um den Ausdruck `ex` zu konstruieren, der die Funktion `+` auf den Wert 1 und die Variable `b` anwendet. Beachten Sie den wichtigen Unterschied in der Art und Weise, wie `a` und `b` verwendet werden:

  * Der Wert der *Variablen* `a` zur Zeit der Ausdruckserstellung wird als unmittelbarer Wert im Ausdruck verwendet. Daher spielt der Wert von `a`, wenn der Ausdruck ausgewertet wird, keine Rolle mehr: Der Wert im Ausdruck ist bereits `1`, unabhängig davon, welchen Wert `a` haben könnte.
  * Andererseits wird das *Symbol* `:b` beim Erstellen des Ausdrucks verwendet, sodass der Wert der Variablen `b` zu diesem Zeitpunkt irrelevant ist – `:b` ist nur ein Symbol und die Variable `b` muss nicht einmal definiert sein. Zum Zeitpunkt der Auswertung des Ausdrucks wird jedoch der Wert des Symbols `:b` ermittelt, indem der Wert der Variablen `b` nachgeschlagen wird.

### Functions on `Expr`essions

As hinted above, one extremely useful feature of Julia is the capability to generate and manipulate Julia code within Julia itself. We have already seen one example of a function returning [`Expr`](@ref) objects: the [`Meta.parse`](@ref) function, which takes a string of Julia code and returns the corresponding `Expr`. A function can also take one or more `Expr` objects as arguments, and return another `Expr`. Here is a simple, motivating example:

```jldoctest
julia> function math_expr(op, op1, op2)
           expr = Expr(:call, op, op1, op2)
           return expr
       end
math_expr (generic function with 1 method)

julia>  ex = math_expr(:+, 1, Expr(:call, :*, 4, 5))
:(1 + 4 * 5)

julia> eval(ex)
21
```

Als weiteres Beispiel hier eine Funktion, die jedes numerische Argument verdoppelt, aber Ausdrücke unberührt lässt:

```jldoctest
julia> function make_expr2(op, opr1, opr2)
           opr1f, opr2f = map(x -> isa(x, Number) ? 2*x : x, (opr1, opr2))
           retexpr = Expr(:call, op, opr1f, opr2f)
           return retexpr
       end
make_expr2 (generic function with 1 method)

julia> make_expr2(:+, 1, 2)
:(2 + 4)

julia> ex = make_expr2(:+, 1, Expr(:call, :*, 5, 8))
:(2 + 5 * 8)

julia> eval(ex)
42
```

## [Macros](@id man-macros)

Makros bieten einen Mechanismus, um generierten Code in den endgültigen Körper eines Programms einzufügen. Ein Makro ordnet ein Tupel von Argumenten einem zurückgegebenen *Ausdruck* zu, und der resultierende Ausdruck wird direkt kompiliert, anstatt einen Runtime-[`eval`](@ref)-Aufruf zu erfordern. Makroargumente können Ausdrücke, Literalwerte und Symbole enthalten.

### Basics

Hier ist ein außergewöhnlich einfaches Makro:

```jldoctest sayhello
julia> macro sayhello()
           return :( println("Hello, world!") )
       end
@sayhello (macro with 1 method)
```

Makros haben ein spezielles Zeichen in Julias Syntax: das `@` (At-Zeichen), gefolgt vom einzigartigen Namen, der in einem `macro NAME ... end`-Block deklariert ist. In diesem Beispiel wird der Compiler alle Instanzen von `@sayhello` ersetzen mit:

```julia
:( println("Hello, world!") )
```

Wenn `@sayhello` im REPL eingegeben wird, wird der Ausdruck sofort ausgeführt, sodass wir nur das Evaluierungsergebnis sehen:

```jldoctest sayhello
julia> @sayhello()
Hello, world!
```

Jetzt betrachten wir ein etwas komplexeres Makro:

```jldoctest sayhello2
julia> macro sayhello(name)
           return :( println("Hello, ", $name) )
       end
@sayhello (macro with 1 method)
```

Dieses Makro nimmt ein Argument: `name`. Wenn `@sayhello` aufgerufen wird, wird der zitierte Ausdruck *erweitert*, um den Wert des Arguments in den endgültigen Ausdruck zu interpolieren:

```jldoctest sayhello2
julia> @sayhello("human")
Hello, human
```

Wir können den zitierten Rückgabewertausdruck mit der Funktion [`macroexpand`](@ref) anzeigen (**wichtiger Hinweis:** Dies ist ein äußerst nützliches Werkzeug zum Debuggen von Makros):

```julia-repl sayhello2
julia> ex = macroexpand(Main, :(@sayhello("human")) )
:(Main.println("Hello, ", "human"))

julia> typeof(ex)
Expr
```

Wir können sehen, dass das `"human"` Literal in den Ausdruck interpoliert wurde.

Es gibt auch ein Makro [`@macroexpand`](@ref), das vielleicht etwas praktischer ist als die Funktion `macroexpand`:

```jldoctest sayhello2
julia> @macroexpand @sayhello "human"
:(println("Hello, ", "human"))
```

### Hold up: why macros?

Wir haben bereits eine Funktion `f(::Expr...) -> Expr` in einem vorherigen Abschnitt gesehen. Tatsächlich ist [`macroexpand`](@ref) ebenfalls eine solche Funktion. Warum gibt es also Makros?

Makros sind notwendig, da sie ausgeführt werden, wenn der Code analysiert wird. Daher ermöglichen Makros dem Programmierer, Fragmente von benutzerdefiniertem Code *vor* der Ausführung des gesamten Programms zu generieren und einzufügen. Um den Unterschied zu veranschaulichen, betrachten Sie das folgende Beispiel:

```julia-repl whymacros
julia> macro twostep(arg)
           println("I execute at parse time. The argument is: ", arg)
           return :(println("I execute at runtime. The argument is: ", $arg))
       end
@twostep (macro with 1 method)

julia> ex = macroexpand(Main, :(@twostep :(1, 2, 3)) );
I execute at parse time. The argument is: :((1, 2, 3))
```

Der erste Aufruf von [`println`](@ref) wird ausgeführt, wenn [`macroexpand`](@ref) aufgerufen wird. Der resultierende Ausdruck enthält *nur* das zweite `println`:

```julia-repl whymacros
julia> typeof(ex)
Expr

julia> ex
:(println("I execute at runtime. The argument is: ", $(Expr(:copyast, :($(QuoteNode(:((1, 2, 3)))))))))

julia> eval(ex)
I execute at runtime. The argument is: (1, 2, 3)
```

### Macro invocation

Makros werden mit der folgenden allgemeinen Syntax aufgerufen:

```julia
@name expr1 expr2 ...
@name(expr1, expr2, ...)
```

Beachten Sie das unterscheidende `@` vor dem Makronamen und das Fehlen von Kommas zwischen den Argumentausdrücken in der ersten Form sowie das Fehlen von Leerzeichen nach `@name` in der zweiten Form. Die beiden Stile sollten nicht gemischt werden. Zum Beispiel ist die folgende Syntax anders als die oben genannten Beispiele; sie übergibt das Tupel `(expr1, expr2, ...)` als ein Argument an das Makro:

```julia
@name (expr1, expr2, ...)
```

Eine alternative Möglichkeit, ein Makro über ein Array-Literal (oder eine Komprehension) aufzurufen, besteht darin, beide ohne Klammern nebeneinander zu stellen. In diesem Fall wird das Array der einzige Ausdruck sein, der dem Makro übergeben wird. Die folgende Syntax ist äquivalent (und unterscheidet sich von `@name [a b] * v`):

```julia
@name[a b] * v
@name([a b]) * v
```

Es ist wichtig zu betonen, dass Makros ihre Argumente als Ausdrücke, Literale oder Symbole erhalten. Eine Möglichkeit, die Makroargumente zu erkunden, besteht darin, die [`show`](@ref)-Funktion innerhalb des Makrokörpers aufzurufen:

```jldoctest
julia> macro showarg(x)
           show(x)
           # ... remainder of macro, returning an expression
       end
@showarg (macro with 1 method)

julia> @showarg(a)
:a

julia> @showarg(1+1)
:(1 + 1)

julia> @showarg(println("Yo!"))
:(println("Yo!"))

julia> @showarg(1)        # Numeric literal
1

julia> @showarg("Yo!")    # String literal
"Yo!"

julia> @showarg("Yo! $("hello")")    # String with interpolation is an Expr rather than a String
:("Yo! $("hello")")
```

Zusätzlich zur angegebenen Argumentliste werden jedem Makro zusätzliche Argumente mit den Namen `__source__` und `__module__` übergeben.

Das Argument `__source__` liefert Informationen (in Form eines `LineNumberNode`-Objekts) über den Parserstandort des `@`-Zeichens aus dem Makroaufruf. Dies ermöglicht es Makros, bessere Fehlermeldungen bereitzustellen und wird häufig von Protokollierungs-, String-Parser-Makros und Dokumentationen verwendet, sowie zur Implementierung der [`@__LINE__`](@ref), [`@__FILE__`](@ref) und [`@__DIR__`](@ref)-Makros.

Die Standortinformationen können durch Verweisen auf `__source__.line` und `__source__.file` abgerufen werden:

```jldoctest
julia> macro __LOCATION__(); return QuoteNode(__source__); end
@__LOCATION__ (macro with 1 method)

julia> dump(
            @__LOCATION__(
       ))
LineNumberNode
  line: Int64 2
  file: Symbol none
```

Das Argument `__module__` liefert Informationen (in Form eines `Module`-Objekts) über den Erweiterungskontext des Makroaufrufs. Dies ermöglicht es Makros, kontextuelle Informationen wie bestehende Bindungen nachzuschlagen oder den Wert als zusätzliches Argument für einen Funktionsaufruf zur Laufzeit einzufügen, der eine Selbstreflexion im aktuellen Modul durchführt.

### Building an advanced macro

Hier ist eine vereinfachte Definition von Julias [`@assert`](@ref) Makro:

```jldoctest building
julia> macro assert(ex)
           return :( $ex ? nothing : throw(AssertionError($(string(ex)))) )
       end
@assert (macro with 1 method)
```

Dieses Makro kann wie folgt verwendet werden:

```jldoctest building
julia> @assert 1 == 1.0

julia> @assert 1 == 0
ERROR: AssertionError: 1 == 0
```

Anstelle der geschriebenen Syntax wird der Makroaufruf zur Parse-Zeit auf das zurückgegebene Ergebnis erweitert. Dies entspricht dem Schreiben von:

```julia
1 == 1.0 ? nothing : throw(AssertionError("1 == 1.0"))
1 == 0 ? nothing : throw(AssertionError("1 == 0"))
```

Das heißt, im ersten Aufruf wird der Ausdruck `:(1 == 1.0)` in den Testbedingungsplatz eingefügt, während der Wert von `string(:(1 == 1.0))` in den Platz für die Assertionsnachricht eingefügt wird. Der gesamte Ausdruck, so konstruiert, wird in den Syntaxbaum eingefügt, wo der Aufruf des `@assert`-Makros erfolgt. Dann, zur Ausführungszeit, wenn der Testausdruck wahr ist, wird [`nothing`](@ref) zurückgegeben, während im Falle, dass der Test falsch ist, ein Fehler ausgelöst wird, der den behaupteten Ausdruck anzeigt, der falsch war. Beachten Sie, dass es nicht möglich wäre, dies als Funktion zu schreiben, da nur der *Wert* der Bedingung verfügbar ist und es unmöglich wäre, den Ausdruck, der ihn berechnet hat, in der Fehlermeldung anzuzeigen.

Die tatsächliche Definition von `@assert` in Julia Base ist komplizierter. Sie ermöglicht es dem Benutzer, optional seine eigene Fehlermeldung anzugeben, anstatt nur den fehlgeschlagenen Ausdruck auszugeben. Genau wie in Funktionen mit einer variablen Anzahl von Argumenten ([Varargs Functions](@ref)) wird dies mit einer Ellipse nach dem letzten Argument angegeben:

```jldoctest assert2
julia> macro assert(ex, msgs...)
           msg_body = isempty(msgs) ? ex : msgs[1]
           msg = string(msg_body)
           return :($ex ? nothing : throw(AssertionError($msg)))
       end
@assert (macro with 1 method)
```

Jetzt hat `@assert` zwei Betriebsmodi, abhängig von der Anzahl der übergebenen Argumente! Wenn nur ein Argument vorhanden ist, wird das Tupel der Ausdrücke, das von `msgs` erfasst wird, leer sein und es verhält sich wie die einfachere Definition oben. Wenn der Benutzer jedoch ein zweites Argument angibt, wird es im Nachrichteninhalt anstelle des fehlerhaften Ausdrucks ausgegeben. Sie können das Ergebnis einer Makroerweiterung mit dem treffend benannten [`@macroexpand`](@ref)-Makro inspizieren:

```julia-repl assert2
julia> @macroexpand @assert a == b
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a == b"))
    end)

julia> @macroexpand @assert a==b "a should equal b!"
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a should equal b!"))
    end)
```

Es gibt noch einen weiteren Fall, den das tatsächliche `@assert`-Makro behandelt: Was ist, wenn wir zusätzlich zu "a sollte b entsprechen" auch ihre Werte drucken möchten? Man könnte naiv versuchen, die String-Interpolation in der benutzerdefinierten Nachricht zu verwenden, z.B. `@assert a==b "a ($a) sollte b ($b) entsprechen!"`, aber das wird mit dem obigen Makro nicht wie erwartet funktionieren. Kannst du sehen, warum? Erinnere dich an [string interpolation](@ref string-interpolation), dass ein interpolierter String in einen Aufruf von [`string`](@ref) umgeschrieben wird. Vergleiche:

```jldoctest
julia> typeof(:("a should equal b"))
String

julia> typeof(:("a ($a) should equal b ($b)!"))
Expr

julia> dump(:("a ($a) should equal b ($b)!"))
Expr
  head: Symbol string
  args: Array{Any}((5,))
    1: String "a ("
    2: Symbol a
    3: String ") should equal b ("
    4: Symbol b
    5: String ")!"
```

So jetzt erhält das Makro anstelle eines einfachen Strings in `msg_body` einen vollständigen Ausdruck, der ausgewertet werden muss, um wie erwartet angezeigt zu werden. Dies kann direkt als Argument in den zurückgegebenen Ausdruck für den [`string`](@ref) Aufruf eingefügt werden; siehe [`error.jl`](https://github.com/JuliaLang/julia/blob/master/base/error.jl) für die vollständige Implementierung.

Das `@assert`-Makro nutzt das Einfügen in zitierte Ausdrücke hervorragend, um die Manipulation von Ausdrücken im Makrokörper zu vereinfachen.

### Hygiene

Ein Problem, das bei komplexeren Makros auftritt, ist das von [hygiene](https://en.wikipedia.org/wiki/Hygienic_macro). Kurz gesagt, Makros müssen sicherstellen, dass die Variablen, die sie in ihren zurückgegebenen Ausdrücken einführen, nicht versehentlich mit bestehenden Variablen im umgebenden Code, in den sie expandieren, in Konflikt geraten. Umgekehrt wird erwartet, dass die Ausdrücke, die als Argumente in ein Makro übergeben werden, im Kontext des umgebenden Codes ausgewertet werden und mit den bestehenden Variablen interagieren und diese modifizieren. Ein weiteres Anliegen ergibt sich aus der Tatsache, dass ein Makro in einem anderen Modul aufgerufen werden kann als dem, in dem es definiert wurde. In diesem Fall müssen wir sicherstellen, dass alle globalen Variablen dem richtigen Modul zugeordnet werden. Julia hat bereits einen großen Vorteil gegenüber Sprachen mit textueller Makroerweiterung (wie C), da es nur den zurückgegebenen Ausdruck berücksichtigen muss. Alle anderen Variablen (wie `msg` in `@assert` oben) folgen dem [normal scoping block behavior](@ref scope-of-variables).

Um diese Probleme zu demonstrieren, lassen Sie uns eine `@time`-Makro betrachten, das einen Ausdruck als Argument nimmt, die Zeit aufzeichnet, den Ausdruck auswertet, die Zeit erneut aufzeichnet, die Differenz zwischen der vorherigen und der nachfolgenden Zeit ausgibt und dann den Wert des Ausdrucks als endgültigen Wert hat. Das Makro könnte so aussehen:

```julia
macro time(ex)
    return quote
        local t0 = time_ns()
        local val = $ex
        local t1 = time_ns()
        println("elapsed time: ", (t1-t0)/1e9, " seconds")
        val
    end
end
```

Hier wollen wir, dass `t0`, `t1` und `val` private temporäre Variablen sind, und wir wollen, dass `time_ns` auf die [`time_ns`](@ref) Funktion in Julia Base verweist, nicht auf irgendeine `time_ns` Variable, die der Benutzer haben könnte (das Gleiche gilt für `println`). Stellen Sie sich die Probleme vor, die auftreten könnten, wenn der Benutzerausdruck `ex` auch Zuweisungen an eine Variable namens `t0` enthielte oder seine eigene `time_ns` Variable definierte. Wir könnten Fehler oder mysteriös falsches Verhalten bekommen.

Julias Makro-Expander löst diese Probleme auf folgende Weise. Zunächst werden Variablen innerhalb eines Makroergebnisses als lokal oder global klassifiziert. Eine Variable wird als lokal betrachtet, wenn sie zugewiesen wird (und nicht als global deklariert ist), lokal deklariert ist oder als Funktionsargumentname verwendet wird. Andernfalls wird sie als global betrachtet. Lokale Variablen werden dann umbenannt, um einzigartig zu sein (unter Verwendung der [`gensym`](@ref)-Funktion, die neue Symbole generiert), und globale Variablen werden innerhalb der Makrodefinitionsumgebung aufgelöst. Daher werden beide oben genannten Anliegen behandelt; die lokalen Variablen des Makros werden nicht mit Benutzervariablen in Konflikt stehen, und `time_ns` sowie `println` beziehen sich auf die Julia Base-Definitionen.

Ein Problem bleibt jedoch bestehen. Betrachten Sie die folgende Verwendung dieses Makros:

```julia
module MyModule
import Base.@time

time_ns() = ... # compute something

@time time_ns()
end
```

Hier bezieht sich der Benutzerausdruck `ex` auf `time_ns`, jedoch nicht auf dieselbe `time_ns`-Funktion, die das Makro verwendet. Es bezieht sich eindeutig auf `MyModule.time_ns`. Daher müssen wir dafür sorgen, dass der Code in `ex` im Makroaufrufumfeld aufgelöst wird. Dies geschieht, indem der Ausdruck mit [`esc`](@ref) "escaped" wird:

```julia
macro time(ex)
    ...
    local val = $(esc(ex))
    ...
end
```

Ein auf diese Weise umschlossenes Ausdruck bleibt vom Makro-Expander unberührt und wird einfach unverändert in die Ausgabe eingefügt. Daher wird es im Makroaufruf-Umfeld aufgelöst.

Dieser Escape-Mechanismus kann verwendet werden, um die Hygiene bei Bedarf zu "verletzen", um Benutzervariablen einzuführen oder zu manipulieren. Zum Beispiel setzt das folgende Makro `x` im Aufrufumfeld auf null:

```jldoctest
julia> macro zerox()
           return esc(:(x = 0))
       end
@zerox (macro with 1 method)

julia> function foo()
           x = 1
           @zerox
           return x # is zero
       end
foo (generic function with 1 method)

julia> foo()
0
```

Diese Art der Manipulation von Variablen sollte mit Bedacht eingesetzt werden, ist aber gelegentlich sehr nützlich.

Die richtigen Hygieneregeln zu beachten, kann eine formidable Herausforderung sein. Bevor Sie ein Makro verwenden, sollten Sie überlegen, ob eine Funktionsclosure ausreichend wäre. Eine weitere nützliche Strategie besteht darin, so viel Arbeit wie möglich zur Laufzeit zu verschieben. Zum Beispiel wickeln viele Makros ihre Argumente einfach in einen `QuoteNode` oder einen anderen ähnlichen [`Expr`](@ref). Einige Beispiele hierfür sind `@task body`, das einfach `schedule(Task(() -> $body))` zurückgibt, und `@eval expr`, das einfach `eval(QuoteNode(expr))` zurückgibt.

Um zu demonstrieren, könnten wir das obige `@time`-Beispiel umschreiben als:

```julia
macro time(expr)
    return :(timeit(() -> $(esc(expr))))
end
function timeit(f)
    t0 = time_ns()
    val = f()
    t1 = time_ns()
    println("elapsed time: ", (t1-t0)/1e9, " seconds")
    return val
end
```

Allerdings tun wir dies aus gutem Grund: Das Einwickeln des `expr` in einen neuen Scope-Block (die anonyme Funktion) ändert auch leicht die Bedeutung des Ausdrucks (den Geltungsbereich der darin enthaltenen Variablen), während wir möchten, dass `@time` mit minimalen Auswirkungen auf den umschlossenen Code verwendbar ist.

### Macros and dispatch

Makros, genau wie Julia-Funktionen, sind generisch. Das bedeutet, dass sie auch mehrere Methodendefinitionen haben können, dank mehrfacher Dispatch:

```jldoctest macromethods
julia> macro m end
@m (macro with 0 methods)

julia> macro m(args...)
           println("$(length(args)) arguments")
       end
@m (macro with 1 method)

julia> macro m(x,y)
           println("Two arguments")
       end
@m (macro with 2 methods)

julia> @m "asd"
1 arguments

julia> @m 1 2
Two arguments
```

Man sollte jedoch im Hinterkopf behalten, dass die Makro-Dispatching auf den Typen des AST basiert, die dem Makro übergeben werden, nicht auf den Typen, die der AST zur Laufzeit auswertet:

```jldoctest macromethods
julia> macro m(::Int)
           println("An Integer")
       end
@m (macro with 3 methods)

julia> @m 2
An Integer

julia> x = 2
2

julia> @m x
1 arguments
```

## Code Generation

Wenn eine erhebliche Menge an sich wiederholendem Boilerplate-Code erforderlich ist, ist es üblich, diesen programmgesteuert zu generieren, um Redundanz zu vermeiden. In den meisten Sprachen erfordert dies einen zusätzlichen Build-Schritt und ein separates Programm zur Generierung des sich wiederholenden Codes. In Julia ermöglichen Ausdrucksinterpolation und [`eval`](@ref) eine solche Codegenerierung im normalen Verlauf der Programmausführung. Betrachten Sie beispielsweise den folgenden benutzerdefinierten Typ.

```jldoctest mynumber-codegen
struct MyNumber
    x::Float64
end
# output

```

für die wir eine Reihe von Methoden hinzufügen möchten. Wir können dies programmgesteuert in der folgenden Schleife tun:

```jldoctest mynumber-codegen
for op = (:sin, :cos, :tan, :log, :exp)
    eval(quote
        Base.$op(a::MyNumber) = MyNumber($op(a.x))
    end)
end
# output

```

und wir können diese Funktionen jetzt mit unserem benutzerdefinierten Typ verwenden:

```jldoctest mynumber-codegen
julia> x = MyNumber(π)
MyNumber(3.141592653589793)

julia> sin(x)
MyNumber(1.2246467991473532e-16)

julia> cos(x)
MyNumber(-1.0)
```

Auf diese Weise fungiert Julia als ihr eigener [preprocessor](https://en.wikipedia.org/wiki/Preprocessor) und ermöglicht die Codegenerierung innerhalb der Sprache. Der obige Code könnte etwas knapper mit der `:`-Präfix-Zitierform geschrieben werden:

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    eval(:(Base.$op(a::MyNumber) = MyNumber($op(a.x))))
end
```

Diese Art der Code-Generierung in der Sprache, die das Muster `eval(quote(...))` verwendet, ist häufig genug, dass Julia mit einem Makro kommt, um dieses Muster abzukürzen:

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    @eval Base.$op(a::MyNumber) = MyNumber($op(a.x))
end
```

Die [`@eval`](@ref)-Makro schreibt diesen Aufruf so um, dass er genau äquivalent zu den oben genannten längeren Versionen ist. Für längere Blöcke von generiertem Code kann das Ausdrucksargument, das an `4d61726b646f776e2e436f64652822222c2022406576616c2229_40726566` übergeben wird, ein Block sein:

```julia
@eval begin
    # multiple lines
end
```

## [Non-Standard String Literals](@id meta-non-standard-string-literals)

Erinnere dich an [Strings](@ref non-standard-string-literals), dass Zeichenfolgenliterale, die mit einem Bezeichner versehen sind, als nicht-standardisierte Zeichenfolgenliterale bezeichnet werden und andere Semantiken haben können als nicht-prefixed Zeichenfolgenliterale. Zum Beispiel:

  * `r"^\s*(?:#|$)"` erzeugt einen [regular expression object](@ref man-regex-literals) anstelle eines Strings.
  * `b"DATA\xff\u2200"` ist ein [byte array literal](@ref man-byte-array-literals) für `[68,65,84,65,255,226,136,128]`.

Vielleicht überraschend sind diese Verhaltensweisen nicht fest im Julia-Parser oder -Compiler codiert. Stattdessen sind sie benutzerdefinierte Verhaltensweisen, die durch einen allgemeinen Mechanismus bereitgestellt werden, den jeder nutzen kann: Präfixierte String-Literale werden als Aufrufe an speziell benannte Makros interpretiert. Zum Beispiel ist das reguläre Ausdrucks-Makro einfach das Folgende:

```julia
macro r_str(p)
    Regex(p)
end
```

Das ist alles. Dieses Makro besagt, dass der wörtliche Inhalt des String-Literals `r"^\s*(?:#|$)"` an das `@r_str`-Makro übergeben werden soll und das Ergebnis dieser Erweiterung an der Stelle im Syntaxbaum platziert werden soll, an der das String-Literal vorkommt. Mit anderen Worten, der Ausdruck `r"^\s*(?:#|$)"` ist gleichbedeutend damit, das folgende Objekt direkt in den Syntaxbaum einzufügen:

```julia
Regex("^\\s*(?:#|\$)")
```

Nicht nur ist die Zeichenfolgenliteralform kürzer und viel praktischer, sondern sie ist auch effizienter: Da der reguläre Ausdruck kompiliert wird und das `Regex`-Objekt tatsächlich *während der Kompilierung des Codes* erstellt wird, erfolgt die Kompilierung nur einmal, anstatt jedes Mal, wenn der Code ausgeführt wird. Betrachten Sie, ob der reguläre Ausdruck in einer Schleife vorkommt:

```julia
for line = lines
    m = match(r"^\s*(?:#|$)", line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

Da der reguläre Ausdruck `r"^\s*(?:#|$)"` kompiliert und in den Syntaxbaum eingefügt wird, wenn dieser Code analysiert wird, wird der Ausdruck nur einmal kompiliert, anstatt jedes Mal, wenn die Schleife ausgeführt wird. Um dies ohne Makros zu erreichen, müsste man diese Schleife folgendermaßen schreiben:

```julia
re = Regex("^\\s*(?:#|\$)")
for line = lines
    m = match(re, line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

Darüber hinaus, wenn der Compiler nicht feststellen konnte, dass das Regex-Objekt über alle Schleifen konstant war, könnten bestimmte Optimierungen möglicherweise nicht möglich sein, was diese Version immer noch weniger effizient macht als die oben genannte bequemere literale Form. Natürlich gibt es immer noch Situationen, in denen die nicht-literal Form praktischer ist: Wenn man eine Variable in den regulären Ausdruck interpolieren muss, muss man diesen umständlicheren Ansatz wählen; in Fällen, in denen das Muster des regulären Ausdrucks selbst dynamisch ist und sich möglicherweise bei jeder Schleifeniteration ändert, muss bei jeder Iteration ein neues reguläres Ausdrucksobjekt erstellt werden. In der überwiegenden Mehrheit der Anwendungsfälle werden jedoch reguläre Ausdrücke nicht basierend auf Laufzeitdaten erstellt. In dieser Mehrheit der Fälle ist die Fähigkeit, reguläre Ausdrücke als Kompilierungszeitwerte zu schreiben, von unschätzbarem Wert.

Der Mechanismus für benutzerdefinierte String-Literale ist tiefgreifend und äußerst mächtig. Nicht nur werden Julias nicht-standardisierte Literale damit implementiert, sondern auch die Syntax für Befehlsliterale (``` `echo "Hallo, $person"` ```) wird mit dem folgenden harmlos aussehenden Makro implementiert:

```julia
macro cmd(str)
    :(cmd_gen($(shell_parse(str)[1])))
end
```

Natürlich ist eine große Menge an Komplexität in den Funktionen verborgen, die in dieser Makrodefinition verwendet werden, aber sie sind nur Funktionen, die vollständig in Julia geschrieben sind. Sie können ihren Quellcode lesen und genau sehen, was sie tun – und alles, was sie tun, ist, Ausdrucksobjekte zu erstellen, die in den Syntaxbaum Ihres Programms eingefügt werden.

Wie Zeichenfolgenliterale können auch Befehlsliterale mit einem Bezeichner vorangestellt werden, um das zu bilden, was als nicht-standardisierte Befehlsliterale bezeichnet wird. Diese Befehlsliterale werden als Aufrufe an speziell benannte Makros interpretiert. Zum Beispiel wird die Syntax ```custom`literal` ``` als `@custom_cmd "literal"` interpretiert. Julia selbst enthält keine nicht-standardisierten Befehlsliterale, aber Pakete können diese Syntax nutzen. Abgesehen von der unterschiedlichen Syntax und dem Suffix `_cmd` anstelle des Suffixes `_str` verhalten sich nicht-standardisierte Befehlsliterale genau wie nicht-standardisierte Zeichenfolgenliterale.

Im Falle, dass zwei Module nicht-standardisierte Zeichenfolgen- oder Befehlsliterale mit demselben Namen bereitstellen, ist es möglich, das Zeichenfolgen- oder Befehlsliteral mit einem Modulnamen zu qualifizieren. Wenn beispielsweise sowohl `Foo` als auch `Bar` das nicht-standardisierte Zeichenfolgenliteral `@x_str` bereitstellen, kann man `Foo.x"literal"` oder `Bar.x"literal"` schreiben, um zwischen den beiden zu unterscheiden.

Eine andere Möglichkeit, ein Makro zu definieren, wäre wie folgt:

```julia
macro foo_str(str, flag)
    # do stuff
end
```

Dieser Makro kann dann mit der folgenden Syntax aufgerufen werden:

```julia
foo"str"flag
```

Der Typ der Flagge in der oben genannten Syntax wäre ein `String` mit dem Inhalt von allem, was nach dem String-Literal folgt.

## Generated functions

Eine ganz besondere Makro ist [`@generated`](@ref), das es Ihnen ermöglicht, sogenannte *generierte Funktionen* zu definieren. Diese haben die Fähigkeit, spezialisierten Code zu generieren, der von den Typen ihrer Argumente abhängt, mit mehr Flexibilität und/oder weniger Code als das, was mit mehrfacher Dispatch erreicht werden kann. Während Makros zur Parse-Zeit mit Ausdrücken arbeiten und nicht auf die Typen ihrer Eingaben zugreifen können, wird eine generierte Funktion zu einem Zeitpunkt erweitert, an dem die Typen der Argumente bekannt sind, die Funktion jedoch noch nicht kompiliert ist.

Statt einige Berechnungen oder Aktionen durchzuführen, gibt eine generierte Funktionsdeklaration einen zitierten Ausdruck zurück, der dann den Körper für die Methode bildet, die den Typen der Argumente entspricht. Wenn eine generierte Funktion aufgerufen wird, wird der Ausdruck, den sie zurückgibt, kompiliert und dann ausgeführt. Um dies effizient zu gestalten, wird das Ergebnis normalerweise zwischengespeichert. Und um dies ableitbar zu machen, ist nur eine begrenzte Teilmenge der Sprache verwendbar. Somit bieten generierte Funktionen eine flexible Möglichkeit, Arbeit von der Laufzeit zur Kompilierzeit zu verlagern, auf Kosten größerer Einschränkungen bei den zulässigen Konstrukten.

Beim Definieren von generierten Funktionen gibt es fünf Hauptunterschiede zu gewöhnlichen Funktionen:

1. Sie annotieren die Funktionsdeklaration mit dem `@generated`-Makro. Dies fügt dem AST einige Informationen hinzu, die dem Compiler mitteilen, dass es sich um eine generierte Funktion handelt.
2. Im Körper der generierten Funktion haben Sie nur Zugriff auf die *Typen* der Argumente – nicht auf deren Werte.
3. Statt etwas zu berechnen oder eine Aktion auszuführen, gibst du einen *zitierten Ausdruck* zurück, der, wenn er ausgewertet wird, das tut, was du möchtest.
4. Generierte Funktionen dürfen nur Funktionen aufrufen, die *vor* der Definition der generierten Funktion definiert wurden. (Das Nichteinhalten dieser Regel kann dazu führen, dass `MethodErrors` auftreten, die sich auf Funktionen aus einer zukünftigen Welt-Ära beziehen.)
5. Generierte Funktionen dürfen keinen nicht-konstanten globalen Zustand *verändern* oder *beobachten* (einschließlich beispielsweise IO, Sperren, nicht-lokale Wörterbücher oder die Verwendung von [`hasmethod`](@ref)). Das bedeutet, sie dürfen nur globale Konstanten lesen und dürfen keine Nebenwirkungen haben. Mit anderen Worten, sie müssen völlig rein sein. Aufgrund einer Implementierungsbeschränkung bedeutet dies auch, dass sie derzeit keinen Closure oder Generator definieren können.

Es ist am einfachsten, dies mit einem Beispiel zu veranschaulichen. Wir können eine generierte Funktion `foo` deklarieren als

```jldoctest generated
julia> @generated function foo(x)
           Core.println(x)
           return :(x * x)
       end
foo (generic function with 1 method)
```

Beachten Sie, dass der Körper einen zitierten Ausdruck zurückgibt, nämlich `:(x * x)`, anstatt nur den Wert von `x * x`.

Aus der Perspektive des Anrufers ist dies identisch mit einer regulären Funktion; tatsächlich müssen Sie nicht wissen, ob Sie eine reguläre oder generierte Funktion aufrufen. Lassen Sie uns sehen, wie sich `foo` verhält:

```jldoctest generated
julia> x = foo(2); # note: output is from println() statement in the body
Int64

julia> x           # now we print x
4

julia> y = foo("bar");
String

julia> y
"barbar"
```

Also sehen wir, dass im Körper der generierten Funktion `x` der *Typ* des übergebenen Arguments ist, und der Wert, der von der generierten Funktion zurückgegeben wird, das Ergebnis der Auswertung des zitierten Ausdrucks ist, den wir aus der Definition zurückgegeben haben, jetzt mit dem *Wert* von `x`.

Was passiert, wenn wir `foo` erneut mit einem Typ auswerten, den wir bereits verwendet haben?

```jldoctest generated
julia> foo(4)
16
```

Beachten Sie, dass es keinen Ausdruck von [`Int64`](@ref) gibt. Wir können sehen, dass der Körper der generierten Funktion hier nur einmal für die spezifische Menge von Argumenttypen ausgeführt wurde und das Ergebnis zwischengespeichert wurde. Danach wurde in diesem Beispiel der Ausdruck, der bei der ersten Invocation von der generierten Funktion zurückgegeben wurde, als Methodenrumpf wiederverwendet. Das tatsächliche Cache-Verhalten ist jedoch eine implementierungsabhängige Leistungsoptimierung, sodass es ungültig ist, sich zu eng auf dieses Verhalten zu verlassen.

Die Anzahl der Male, die eine generierte Funktion generiert wird, *kann* nur einmal sein, aber sie *kann* auch öfter sein oder anscheinend überhaupt nicht auftreten. Infolgedessen sollten Sie *niemals* eine generierte Funktion mit Nebenwirkungen schreiben - wann und wie oft die Nebenwirkungen auftreten, ist undefiniert. (Das gilt auch für Makros - und genau wie bei Makros ist die Verwendung von [`eval`](@ref) in einer generierten Funktion ein Zeichen dafür, dass Sie es auf die falsche Weise tun.) Im Gegensatz zu Makros kann jedoch das Laufzeitsystem einen Aufruf von `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566` nicht korrekt verarbeiten, daher ist er nicht erlaubt.

Es ist auch wichtig zu sehen, wie `@generated`-Funktionen mit der Methoden-Neudefinition interagieren. Nach dem Prinzip, dass eine korrekte `@generated`-Funktion keinen veränderlichen Zustand beobachten oder eine Mutation des globalen Zustands verursachen darf, sehen wir das folgende Verhalten. Beachten Sie, dass die generierte Funktion *keine* Methode aufrufen kann, die nicht vor der *Definition* der generierten Funktion selbst definiert wurde.

Ursprünglich hat `f(x)` eine Definition

```jldoctest redefinition
julia> f(x) = "original definition";
```

Definieren Sie andere Operationen, die `f(x)` verwenden:

```jldoctest redefinition
julia> g(x) = f(x);

julia> @generated gen1(x) = f(x);

julia> @generated gen2(x) = :(f(x));
```

Wir fügen nun einige neue Definitionen für `f(x)` hinzu:

```jldoctest redefinition
julia> f(x::Int) = "definition for Int";

julia> f(x::Type{Int}) = "definition for Type{Int}";
```

und vergleichen, wie sich diese Ergebnisse unterscheiden:

```jldoctest redefinition
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> gen1(1)
"original definition"

julia> gen2(1)
"definition for Int"
```

Jede Methode einer generierten Funktion hat ihre eigene Sicht auf die definierten Funktionen:

```jldoctest redefinition
julia> @generated gen1(x::Real) = f(x);

julia> gen1(1)
"definition for Type{Int}"
```

Die oben generierte Funktion `foo` hat nichts getan, was eine normale Funktion `foo(x) = x * x` nicht auch tun könnte (außer den Typ bei der ersten Aufruf zu drucken und höhere Kosten zu verursachen). Die Stärke einer generierten Funktion liegt jedoch in ihrer Fähigkeit, je nach den übergebenen Typen unterschiedliche zitierte Ausdrücke zu berechnen:

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```

(obwohl dieses konstruierte Beispiel natürlich leichter mit Mehrfachdispatch umgesetzt werden könnte...)

Missbrauch davon wird das Laufzeitsystem beschädigen und zu undefiniertem Verhalten führen:

```jldoctest
julia> @generated function baz(x)
           if rand() < .9
               return :(x^2)
           else
               return :("boo!")
           end
       end
baz (generic function with 1 method)
```

Da der Körper der generierten Funktion nicht deterministisch ist, ist ihr Verhalten, *und das Verhalten aller nachfolgenden Codes* undefiniert.

*Kopiere diese Beispiele nicht!*

Diese Beispiele sind hoffentlich hilfreich, um zu veranschaulichen, wie generierte Funktionen funktionieren, sowohl am Ende der Definition als auch am Aufrufort; jedoch *kopiere sie nicht*, aus den folgenden Gründen:

  * die `foo`-Funktion hat Nebenwirkungen (der Aufruf von `Core.println`), und es ist undefiniert, wann, wie oft oder wie viele Male diese Nebenwirkungen auftreten werden.
  * die `bar`-Funktion löst ein Problem, das besser mit Mehrfachdispatch gelöst werden kann - die Definition `bar(x) = x` und `bar(x::Integer) = x ^ 2` wird dasselbe tun, ist jedoch sowohl einfacher als auch schneller.
  * die `baz`-Funktion ist pathologisch

Beachten Sie, dass die Menge der Operationen, die in einer generierten Funktion nicht versucht werden sollten, unbegrenzt ist, und das Laufzeitsystem derzeit nur eine Teilmenge der ungültigen Operationen erkennen kann. Es gibt viele andere Operationen, die das Laufzeitsystem einfach ohne Benachrichtigung beschädigen, normalerweise auf subtile Weise, die nicht offensichtlich mit der schlechten Definition verbunden sind. Da der Funktionsgenerator während der Inferenz ausgeführt wird, muss er alle Einschränkungen dieses Codes respektieren.

Einige Operationen, die nicht versucht werden sollten, sind:

1. Caching von nativen Zeigern.
2. Interaktion mit den Inhalten oder Methoden von `Core.Compiler` auf irgendeine Weise.
3. Beobachtung eines veränderlichen Zustands.

      * Die Inferenz der generierten Funktion kann *jederzeit* durchgeführt werden, einschließlich während Ihr Code versucht, diesen Zustand zu beobachten oder zu verändern.
4. Das Halten von Sperren: C-Code, den Sie aufrufen, kann intern Sperren verwenden (zum Beispiel ist es nicht problematisch, `malloc` aufzurufen, obwohl die meisten Implementierungen intern Sperren erfordern), aber versuchen Sie nicht, während der Ausführung von Julia-Code Sperren zu halten oder zu erwerben.
5. Aufruf einer Funktion, die nach dem Körper der generierten Funktion definiert ist. Diese Bedingung wird für inkrementell geladene vorcompilierte Module gelockert, um den Aufruf jeder Funktion im Modul zu ermöglichen.

In Ordnung, jetzt, da wir ein besseres Verständnis dafür haben, wie generierte Funktionen funktionieren, lassen Sie uns diese nutzen, um einige fortgeschrittene (und gültige) Funktionen zu erstellen...

### An advanced example

Julias Basisbibliothek hat eine interne Funktion `sub2ind`, um einen linearen Index in ein n-dimensionales Array zu berechnen, basierend auf einer Menge von n mehrdimensionalen Indizes - mit anderen Worten, um den Index `i` zu berechnen, der verwendet werden kann, um in ein Array `A` mit `A[i]` zu indizieren, anstatt `A[x,y,z,...]`. Eine mögliche Implementierung ist die folgende:

```jldoctest sub2ind
julia> function sub2ind_loop(dims::NTuple{N}, I::Integer...) where N
           ind = I[N] - 1
           for i = N-1:-1:1
               ind = I[i]-1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> sub2ind_loop((3, 5), 1, 2)
4
```

Das gleiche kann mit Rekursion erreicht werden:

```jldoctest
julia> sub2ind_rec(dims::Tuple{}) = 1;

julia> sub2ind_rec(dims::Tuple{}, i1::Integer, I::Integer...) =
           i1 == 1 ? sub2ind_rec(dims, I...) : throw(BoundsError());

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer) = i1;

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer, I::Integer...) =
           i1 + dims[1] * (sub2ind_rec(Base.tail(dims), I...) - 1);

julia> sub2ind_rec((3, 5), 1, 2)
4
```

Beide diese Implementierungen, obwohl unterschiedlich, tun im Wesentlichen dasselbe: eine Laufzeitschleife über die Dimensionen des Arrays, die den Offset in jeder Dimension in den endgültigen Index sammelt.

Allerdings sind alle Informationen, die wir für die Schleife benötigen, in den Typinformationen der Argumente eingebettet. Dies ermöglicht es dem Compiler, die Iteration zur Compile-Zeit zu verschieben und die Laufzeitschleifen vollständig zu eliminieren. Wir können generierte Funktionen nutzen, um einen ähnlichen Effekt zu erzielen; in der Fachsprache des Compilers verwenden wir generierte Funktionen, um die Schleife manuell zu entrollen. Der Körper wird fast identisch, aber anstatt den linearen Index zu berechnen, erstellen wir einen *Ausdruck*, der den Index berechnet:

```jldoctest sub2ind_gen
julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

**Welcher Code wird dadurch generiert?**

Eine einfache Möglichkeit, dies herauszufinden, besteht darin, den Körper in eine andere (reguläre) Funktion zu extrahieren:

```jldoctest sub2ind_gen2
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           length(I) == N || return :(error("partial indexing is unsupported"))
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           return sub2ind_gen_impl(dims, I...)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

Wir können jetzt `sub2ind_gen_impl` ausführen und den Ausdruck untersuchen, den es zurückgibt:

```jldoctest sub2ind_gen2
julia> sub2ind_gen_impl(Tuple{Int,Int}, Int, Int)
:(((I[1] - 1) + dims[1] * (I[2] - 1)) + 1)
```

Also, der Methodenrumpf, der hier verwendet wird, enthält überhaupt keine Schleife - nur das Indizieren in die beiden Tupel, Multiplikation und Addition/Subtraktion. Alle Schleifen werden zur Compile-Zeit ausgeführt, und wir vermeiden Schleifen während der Ausführung vollständig. Daher schleifen wir nur *einmal pro Typ*, in diesem Fall einmal pro `N` (außer in Grenzfällen, in denen die Funktion mehr als einmal generiert wird - siehe Haftungsausschluss oben).

### Optionally-generated functions

Generierte Funktionen können zur Laufzeit eine hohe Effizienz erreichen, bringen jedoch Kosten zur Kompilierzeit mit sich: Für jede Kombination von konkreten Argumenttypen muss ein neuer Funktionskörper generiert werden. Typischerweise ist Julia in der Lage, "generische" Versionen von Funktionen zu kompilieren, die für beliebige Argumente funktionieren, aber bei generierten Funktionen ist dies unmöglich. Das bedeutet, dass Programme, die stark auf generierte Funktionen angewiesen sind, möglicherweise nicht statisch kompiliert werden können.

Um dieses Problem zu lösen, bietet die Sprache eine Syntax zum Schreiben normaler, nicht generierter alternative Implementierungen von generierten Funktionen. Angewendet auf das obige Beispiel `sub2ind` würde es so aussehen:

```jldoctest sub2ind_gen_opt
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> function sub2ind_gen_fallback(dims::NTuple{N}, I) where N
           ind = I[N] - 1
           for i = (N - 1):-1:1
               ind = I[i] - 1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           length(I) == N || error("partial indexing is unsupported")
           if @generated
               return sub2ind_gen_impl(dims, I...)
           else
               return sub2ind_gen_fallback(dims, I)
           end
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

Internally erstellt dieser Code zwei Implementierungen der Funktion: eine generierte, bei der der erste Block in `if @generated` verwendet wird, und eine normale, bei der der `else`-Block verwendet wird. Innerhalb des `then`-Teils des `if @generated`-Blocks hat der Code dieselbe Semantik wie andere generierte Funktionen: Die Argumentnamen beziehen sich auf Typen, und der Code sollte einen Ausdruck zurückgeben. Mehrere `if @generated`-Blöcke können auftreten, in welchem Fall die generierte Implementierung alle `then`-Blöcke verwendet und die alternative Implementierung alle `else`-Blöcke verwendet.

Beachten Sie, dass wir eine Fehlerüberprüfung an den Anfang der Funktion hinzugefügt haben. Dieser Code wird in beiden Versionen gemeinsam sein und ist zur Laufzeit in beiden Versionen aktiv (er wird zitiert und als Ausdruck aus der generierten Version zurückgegeben). Das bedeutet, dass die Werte und Typen der lokalen Variablen zur Zeit der Codegenerierung nicht verfügbar sind – der Codegenerierungscode kann nur die Typen der Argumente sehen.

In diesem Stil der Definition ist die Codegenerierungsfunktion im Wesentlichen eine optionale Optimierung. Der Compiler wird sie verwenden, wenn es günstig ist, kann sich aber andernfalls entscheiden, stattdessen die normale Implementierung zu verwenden. Dieser Stil wird bevorzugt, da er dem Compiler ermöglicht, mehr Entscheidungen zu treffen und Programme auf vielfältigere Weise zu kompilieren, und da normaler Code lesbarer ist als codegenerierender Code. Allerdings hängt es von den Implementierungsdetails des Compilers ab, welche Implementierung verwendet wird, daher ist es entscheidend, dass sich die beiden Implementierungen identisch verhalten.
