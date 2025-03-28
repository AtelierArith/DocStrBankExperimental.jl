# Frequently Asked Questions

## General

### Is Julia named after someone or something?

Nein.

### Why don't you compile Matlab/Python/R/… code to Julia?

Da viele Menschen mit der Syntax anderer dynamischer Sprachen vertraut sind und bereits viel Code in diesen Sprachen geschrieben wurde, ist es nur natürlich, sich zu fragen, warum wir nicht einfach ein Matlab- oder Python-Frontend in ein Julia-Backend integrieren (oder Code nach Julia "transpilieren"), um alle Leistungs Vorteile von Julia zu nutzen, ohne dass Programmierer eine neue Sprache lernen müssen. Einfach, oder?

Das grundlegende Problem ist, dass es *nichts Besonderes an Julias Compiler gibt*: Wir verwenden einen alltäglichen Compiler (LLVM) ohne „geheime Zutat“, die andere Sprachentwickler nicht kennen. Tatsächlich ist Julias Compiler in vielerlei Hinsicht viel einfacher als die anderer dynamischer Sprachen (z. B. PyPy oder LuaJIT). Julias Leistungs Vorteil ergibt sich fast ausschließlich aus seinem Front-End: Seine Sprachsemantik ermöglicht es einem [well-written Julia program](@ref man-performance-tips), *dem Compiler mehr Möglichkeiten zu geben*, um effizienten Code und Speicherlayouts zu generieren. Wenn Sie versuchen würden, Matlab- oder Python-Code nach Julia zu kompilieren, wäre unser Compiler durch die Semantik von Matlab oder Python darauf beschränkt, Code zu produzieren, der nicht besser ist als der bestehender Compiler für diese Sprachen (und wahrscheinlich schlechter). Die Schlüsselrolle der Semantik ist auch der Grund, warum mehrere bestehende Python-Compiler (wie Numba und Pythran) nur versuchen, einen kleinen Teil der Sprache zu optimieren (z. B. Operationen auf Numpy-Arrays und Skalaren), und für dieses Teilset schneiden sie bereits mindestens so gut ab, wie wir es für die gleiche Semantik könnten. Die Menschen, die an diesen Projekten arbeiten, sind unglaublich klug und haben erstaunliche Dinge erreicht, aber einen Compiler auf eine Sprache anzupassen, die zum Interpretieren entworfen wurde, ist ein sehr schwieriges Problem.

Julias Vorteil ist, dass gute Leistung nicht auf eine kleine Teilmenge von „eingebauten“ Typen und Operationen beschränkt ist, und man kann hochgradig typ-genericen Code schreiben, der auf beliebigen benutzerdefinierten Typen funktioniert, während er schnell und speichereffizient bleibt. Typen in Sprachen wie Python bieten dem Compiler einfach nicht genügend Informationen für ähnliche Fähigkeiten, sodass man, sobald man diese Sprachen als Front-End für Julia verwendet, feststecken würde.

Aus ähnlichen Gründen würde eine automatisierte Übersetzung nach Julia typischerweise unleserlichen, langsamen, nicht-idiomatischen Code erzeugen, der keinen guten Ausgangspunkt für einen nativen Julia-Port aus einer anderen Sprache darstellen würde.

Andererseits ist die *Interoperabilität* von Sprachen äußerst nützlich: Wir wollen bestehenden hochwertigen Code in anderen Sprachen aus Julia (und umgekehrt) nutzen! Der beste Weg, dies zu ermöglichen, ist nicht ein Transpiler, sondern vielmehr einfache intersprachliche Aufrufmöglichkeiten. Wir haben hart daran gearbeitet, von der eingebauten `ccall`-Funktion (um C- und Fortran-Bibliotheken aufzurufen) bis zu [JuliaInterop](https://github.com/JuliaInterop)-Paketen, die Julia mit Python, Matlab, C++ und mehr verbinden.

## [Public API](@id man-api)

### How does Julia define its public API?

Julias öffentliche [API](https://en.wikipedia.org/wiki/API) ist das Verhalten, das in der Dokumentation öffentlicher Symbole aus `Base` und den Standardbibliotheken beschrieben ist. Funktionen, Typen und Konstanten sind kein Teil der öffentlichen API, wenn sie nicht öffentlich sind, selbst wenn sie Docstrings haben oder in der Dokumentation beschrieben sind. Darüber hinaus ist nur das dokumentierte Verhalten öffentlicher Symbole Teil der öffentlichen API. Undokumentiertes Verhalten öffentlicher Symbole ist intern.

Öffentliche Symbole sind diejenigen, die entweder mit `public foo` oder `export foo` gekennzeichnet sind.

Mit anderen Worten:

  * Die dokumentierte Verhalten öffentlicher Symbole ist Teil der öffentlichen API.
  * Undokumentiertes Verhalten öffentlicher Symbole ist nicht Teil der öffentlichen API.
  * Die dokumentierte Funktionsweise privater Symbole ist nicht Teil der öffentlichen API.
  * Das undokumentierte Verhalten privater Symbole ist nicht Teil der öffentlichen API.

Sie können eine vollständige Liste der öffentlichen Symbole aus einem Modul mit `names(MyModule)` erhalten.

Paketautoren werden ermutigt, ihre öffentliche API ähnlich zu definieren.

Alles in Julias öffentlicher API ist durch [SemVer](https://semver.org/) abgedeckt und wird daher vor Julia 2.0 nicht entfernt oder erhält bedeutende, brechende Änderungen.

### There is a useful undocumented function/type/constant. Can I use it?

Das Aktualisieren von Julia kann Ihren Code brechen, wenn Sie nicht-öffentliche APIs verwenden. Wenn der Code eigenständig ist, kann es eine gute Idee sein, ihn in Ihr Projekt zu kopieren. Wenn Sie auf eine komplexe nicht-öffentliche API angewiesen sind, insbesondere wenn Sie sie aus einem stabilen Paket verwenden, ist es eine gute Idee, ein [issue](https://github.com/JuliaLang/julia/issues) oder [pull request](https://github.com/JuliaLang/julia/pulls) zu eröffnen, um eine Diskussion über die Umwandlung in eine öffentliche API zu beginnen. Wir discouragieren jedoch nicht den Versuch, Pakete zu erstellen, die stabile öffentliche Schnittstellen bereitstellen, während sie sich auf nicht-öffentliche Implementierungsdetails von Julia stützen und die Unterschiede zwischen verschiedenen Julia-Versionen abpuffern.

### The documentation is not accurate enough. Can I rely on the existing behavior?

Please open an [issue](https://github.com/JuliaLang/julia/issues) or [pull request](https://github.com/JuliaLang/julia/pulls) to start a discussion for turning the existing behavior into a public API.

## Sessions and the REPL

### How do I delete an object in memory?

Julia hat kein Pendant zur `clear`-Funktion von MATLAB; sobald ein Name in einer Julia-Sitzung (technisch gesehen im Modul `Main`) definiert ist, ist er immer vorhanden.

Wenn der Speicherverbrauch für Sie ein Anliegen ist, können Sie Objekte immer durch solche ersetzen, die weniger Speicher verbrauchen. Zum Beispiel, wenn `A` ein gigabyte-großes Array ist, das Sie nicht mehr benötigen, können Sie den Speicher mit `A = nichts` freigeben. Der Speicher wird beim nächsten Lauf des Garbage Collectors freigegeben; Sie können dies erzwingen, indem Sie [`GC.gc()`](@ref Base.GC.gc) verwenden. Darüber hinaus wird ein Versuch, `A` zu verwenden, wahrscheinlich zu einem Fehler führen, da die meisten Methoden nicht für den Typ `Nichts` definiert sind.

### How can I modify the declaration of a type in my session?

Vielleicht haben Sie einen Typ definiert und stellen dann fest, dass Sie ein neues Feld hinzufügen müssen. Wenn Sie dies im REPL versuchen, erhalten Sie den Fehler:

```
ERROR: invalid redefinition of constant MyType
```

Typen im Modul `Main` können nicht neu definiert werden.

Während dies beim Entwickeln neuer Codes unpraktisch sein kann, gibt es eine ausgezeichnete Lösung. Module können durch Neudefinition ersetzt werden, und wenn Sie Ihren gesamten neuen Code in ein Modul einfügen, können Sie Typen und Konstanten neu definieren. Sie können die Typnamen nicht in `Main` importieren und dann erwarten, dass Sie sie dort neu definieren können, aber Sie können den Modulnamen verwenden, um den Geltungsbereich aufzulösen. Mit anderen Worten, während der Entwicklung könnten Sie einen Workflow verwenden, der etwa so aussieht:

```julia
include("mynewcode.jl")              # this defines a module MyModule
obj1 = MyModule.ObjConstructor(a, b)
obj2 = MyModule.somefunction(obj1)
# Got an error. Change something in "mynewcode.jl"
include("mynewcode.jl")              # reload the module
obj1 = MyModule.ObjConstructor(a, b) # old objects are no longer valid, must reconstruct
obj2 = MyModule.somefunction(obj1)   # this time it worked!
obj3 = MyModule.someotherfunction(obj2, c)
...
```

## [Scripting](@id man-scripting)

### How do I check if the current file is being run as the main script?

Wenn eine Datei als Hauptskript mit `julia file.jl` ausgeführt wird, möchte man möglicherweise zusätzliche Funktionen wie die Verarbeitung von Befehlszeilenargumenten aktivieren. Eine Möglichkeit, festzustellen, ob eine Datei auf diese Weise ausgeführt wird, besteht darin, zu überprüfen, ob `abspath(PROGRAM_FILE) == @__FILE__` `true` ist.

Es wird jedoch empfohlen, keine Dateien zu schreiben, die sowohl als Skript als auch als importierbare Bibliothek fungieren. Wenn man sowohl die Funktionalität einer Bibliothek als auch eines Skripts benötigt, ist es besser, sie als Bibliothek zu schreiben und dann die Funktionalität in ein separates Skript zu importieren.

### [How do I catch CTRL-C in a script?](@id catch-ctrl-c)

Das Ausführen eines Julia-Skripts mit `julia file.jl` wirft nicht [`InterruptException`](@ref), wenn Sie versuchen, es mit CTRL-C (SIGINT) zu beenden. Um einen bestimmten Code vor der Beendigung eines Julia-Skripts auszuführen, der möglicherweise durch CTRL-C verursacht wird oder nicht, verwenden Sie [`atexit`](@ref). Alternativ können Sie `julia -e 'include(popfirst!(ARGS))' file.jl` verwenden, um ein Skript auszuführen, während Sie `InterruptException` im [`try`](@ref)-Block abfangen können. Beachten Sie, dass mit dieser Strategie [`PROGRAM_FILE`](@ref) nicht gesetzt wird.

### How do I pass options to `julia` using `#!/usr/bin/env`?

Das Übergeben von Optionen an `julia` in einer sogenannten Shebang-Zeile, wie in `#!/usr/bin/env julia --startup-file=no`, funktioniert auf vielen Plattformen (BSD, macOS, Linux) nicht, da der Kernel im Gegensatz zur Shell Argumente nicht an Leerzeichen trennt. Die Option `env -S`, die einen einzelnen Argumentstring an Leerzeichen in mehrere Argumente aufteilt, ähnlich wie eine Shell, bietet eine einfache Lösung:

```julia
#!/usr/bin/env -S julia --color=yes --startup-file=no
@show ARGS  # put any Julia code here
```

!!! note
    Option `env -S` erschien in FreeBSD 6.0 (2005), macOS Sierra (2016) und GNU/Linux coreutils 8.30 (2018).


### Why doesn't `run` support `*` or pipes for scripting external programs?

Julias [`run`](@ref) Funktion startet externe Programme *direkt*, ohne ein [operating-system shell](https://en.wikipedia.org/wiki/Shell_(computing)) aufzurufen (im Gegensatz zur `system("...")` Funktion in anderen Sprachen wie Python, R oder C). Das bedeutet, dass `run` keine Wildcard-Erweiterung von `*` (["globbing"](https://en.wikipedia.org/wiki/Glob_(programming))), noch interpretiert es [shell pipelines](https://en.wikipedia.org/wiki/Pipeline_(Unix)) wie `|` oder `>`.

Sie können jedoch weiterhin Globbing und Pipelines mit Julia-Funktionen durchführen. Zum Beispiel ermöglicht die eingebaute [`pipeline`](@ref)-Funktion das Verketten externer Programme und Dateien, ähnlich wie bei Shell-Pipes, und die [Glob.jl package](https://github.com/vtjnash/Glob.jl) implementiert POSIX-kompatibles Globbing.

Sie können natürlich Programme über die Shell ausführen, indem Sie explizit eine Shell und einen Befehlsstring an `run` übergeben, z. B. ```run(`sh -c "ls > files.txt"`)``` um die Unix [Bourne shell](https://en.wikipedia.org/wiki/Bourne_shell) zu verwenden, aber Sie sollten im Allgemeinen reines Julia-Scripting wie ```run(pipeline(`ls`, "files.txt"))``` bevorzugen. Der Grund, warum wir die Shell standardmäßig vermeiden, ist, dass [shelling out sucks](https://julialang.org/blog/2012/03/shelling-out-sucks/): Prozesse über die Shell zu starten, langsam, anfällig für die Zitierung von Sonderzeichen, eine schlechte Fehlerbehandlung hat und problematisch für die Portabilität ist. (Die Python-Entwickler kamen zu einer [similar conclusion](https://www.python.org/dev/peps/pep-0324/#motivation).)

## Variables and Assignments

### Why am I getting `UndefVarError` from a simple loop?

Du könntest etwas haben wie:

```
x = 0
while x < 10
    x += 1
end
```

und beachten Sie, dass es in einer interaktiven Umgebung (wie der Julia REPL) gut funktioniert, aber ```UndefVarError: `x` nicht definiert``` gibt, wenn Sie versuchen, es in einem Skript oder einer anderen Datei auszuführen. Was passiert, ist, dass Julia im Allgemeinen erfordert, dass Sie **explizit sein müssen, wenn Sie in einem lokalen Geltungsbereich globalen Variablen zuweisen**.

Hier ist `x` eine globale Variable, `while` definiert eine [local scope](@ref scope-of-variables), und `x += 1` ist eine Zuweisung an eine globale Variable in diesem lokalen Gültigkeitsbereich.

Wie oben erwähnt, erlaubt Julia (Version 1.5 oder später) das Weglassen des `global`-Schlüsselworts für Code im REPL (und vielen anderen interaktiven Umgebungen), um die Erkundung zu vereinfachen (z. B. das Kopieren und Einfügen von Code aus einer Funktion, um ihn interaktiv auszuführen). Sobald Sie jedoch zu Code in Dateien wechseln, erfordert Julia einen disziplinierteren Umgang mit globalen Variablen. Sie haben mindestens drei Optionen:

1. Setze den Code in eine Funktion (so dass `x` eine *lokale* Variable in einer Funktion ist). Im Allgemeinen ist es gute Softwaretechnik, Funktionen anstelle von globalen Skripten zu verwenden (suche online nach "warum globale Variablen schlecht sind", um viele Erklärungen zu sehen). In Julia sind globale Variablen ebenfalls [slow](@ref man-performance-tips).
2. Wrap the code in a [`let`](@ref) block.  (This makes `x` a local variable within the `let ... end` statement, again eliminating the need for `global`).
3. Markiere `x` ausdrücklich als `global` im lokalen Geltungsbereich, bevor du es zuweist, z.B. schreibe `global x += 1`.

Weitere Erklärungen finden Sie im Handbuchabschnitt [on soft scope](@ref on-soft-scope).

## Functions

### I passed an argument `x` to a function, modified it inside that function, but on the outside, the variable `x` is still unchanged. Why?

Angenommen, Sie rufen eine Funktion wie folgt auf:

```jldoctest
julia> x = 10
10

julia> function change_value!(y)
           y = 17
       end
change_value! (generic function with 1 method)

julia> change_value!(x)
17

julia> x # x is unchanged!
10
```

In Julia kann die Bindung einer Variablen `x` nicht geändert werden, indem `x` als Argument an eine Funktion übergeben wird. Wenn `change_value!(x)` im obigen Beispiel aufgerufen wird, ist `y` eine neu erstellte Variable, die zunächst an den Wert von `x` gebunden ist, d.h. `10`; dann wird `y` an die Konstante `17` neu gebunden, während die Variable `x` des äußeren Geltungsbereichs unberührt bleibt.

Wenn `x` jedoch an ein Objekt vom Typ `Array` (oder einen anderen *veränderbaren* Typ) gebunden ist. Innerhalb der Funktion können Sie `x` nicht von diesem Array "lösen", aber Sie *können* seinen Inhalt ändern. Zum Beispiel:

```jldoctest
julia> x = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> function change_array!(A)
           A[1] = 5
       end
change_array! (generic function with 1 method)

julia> change_array!(x)
5

julia> x
3-element Vector{Int64}:
 5
 2
 3
```

Hier haben wir eine Funktion `change_array!` erstellt, die `5` dem ersten Element des übergebenen Arrays zuweist (gebunden an `x` am Aufrufort und gebunden an `A` innerhalb der Funktion). Beachten Sie, dass `x` nach dem Funktionsaufruf weiterhin an dasselbe Array gebunden ist, aber der Inhalt dieses Arrays sich geändert hat: Die Variablen `A` und `x` waren unterschiedliche Bindungen, die auf dasselbe veränderbare `Array`-Objekt verwiesen.

### Can I use `using` or `import` inside a function?

Nein, es ist nicht erlaubt, eine `using`- oder `import`-Anweisung innerhalb einer Funktion zu haben. Wenn Sie ein Modul importieren möchten, aber dessen Symbole nur innerhalb einer bestimmten Funktion oder einer Gruppe von Funktionen verwenden möchten, haben Sie zwei Optionen:

1. Verwenden Sie `import`:

    ```julia
    import Foo
    function bar(...)
        # ... refer to Foo symbols via Foo.baz ...
    end
    ```

    Dies lädt das Modul `Foo` und definiert eine Variable `Foo`, die auf das Modul verweist, importiert jedoch keine der anderen Symbole aus dem Modul in den aktuellen Namensraum. Sie beziehen sich auf die `Foo`-Symbole mit ihren qualifizierten Namen `Foo.bar` usw.
2. Wickeln Sie Ihre Funktion in ein Modul ein:

    ```julia
    module Bar
    export bar
    using Foo
    function bar(...)
        # ... refer to Foo.baz as simply baz ....
    end
    end
    using Bar
    ```

    Dies importiert alle Symbole aus `Foo`, aber nur innerhalb des Moduls `Bar`.

### What does the `...` operator do?

#### The two uses of the `...` operator: slurping and splatting

Viele Neueinsteiger in Julia finden die Verwendung des `...`-Operators verwirrend. Ein Teil dessen, was den `...`-Operator verwirrend macht, ist, dass er je nach Kontext zwei verschiedene Bedeutungen hat.

#### `...` combines many arguments into one argument in function definitions

Im Kontext von Funktionsdefinitionen wird der `...`-Operator verwendet, um viele verschiedene Argumente zu einem einzigen Argument zu kombinieren. Diese Verwendung von `...` zum Kombinieren vieler verschiedener Argumente zu einem einzigen Argument wird als Slurping bezeichnet:

```jldoctest
julia> function printargs(args...)
           println(typeof(args))
           for (i, arg) in enumerate(args)
               println("Arg #$i = $arg")
           end
       end
printargs (generic function with 1 method)

julia> printargs(1, 2, 3)
Tuple{Int64, Int64, Int64}
Arg #1 = 1
Arg #2 = 2
Arg #3 = 3
```

Wenn Julia eine Sprache wäre, die liberaler mit ASCII-Zeichen umgeht, könnte der Slurp-Operator als `<-...` anstelle von `...` geschrieben worden sein.

#### `...` splits one argument into many different arguments in function calls

Im Gegensatz zur Verwendung des `...`-Operators, um viele verschiedene Argumente in ein Argument zu slurpen, wenn eine Funktion definiert wird, wird der `...`-Operator auch verwendet, um ein einzelnes Funktionsargument in viele verschiedene Argumente zu zerlegen, wenn er im Kontext eines Funktionsaufrufs verwendet wird. Diese Verwendung von `...` wird als Splatting bezeichnet:

```jldoctest
julia> function threeargs(a, b, c)
           println("a = $a::$(typeof(a))")
           println("b = $b::$(typeof(b))")
           println("c = $c::$(typeof(c))")
       end
threeargs (generic function with 1 method)

julia> x = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> threeargs(x...)
a = 1::Int64
b = 2::Int64
c = 3::Int64
```

Wenn Julia eine Sprache wäre, die liberaler mit ASCII-Zeichen umgeht, könnte der Splat-Operator als `...->` anstelle von `...` geschrieben worden sein.

### What is the return value of an assignment?

Der Operator `=` gibt immer die rechte Seite zurück, daher:

```jldoctest
julia> function threeint()
           x::Int = 3.0
           x # returns variable x
       end
threeint (generic function with 1 method)

julia> function threefloat()
           x::Int = 3.0 # returns 3.0
       end
threefloat (generic function with 1 method)

julia> threeint()
3

julia> threefloat()
3.0
```

und ähnlich:

```jldoctest
julia> function twothreetup()
           x, y = [2, 3] # assigns 2 to x and 3 to y
           x, y # returns a tuple
       end
twothreetup (generic function with 1 method)

julia> function twothreearr()
           x, y = [2, 3] # returns an array
       end
twothreearr (generic function with 1 method)

julia> twothreetup()
(2, 3)

julia> twothreearr()
2-element Vector{Int64}:
 2
 3
```

## Types, type declarations, and constructors

### [What does "type-stable" mean?](@id man-type-stability)

Es bedeutet, dass der Typ der Ausgabe vorhersehbar ist aus den Typen der Eingaben. Insbesondere bedeutet es, dass der Typ der Ausgabe nicht variieren kann, abhängig von den *Werten* der Eingaben. Der folgende Code ist *nicht* typstabil:

```jldoctest
julia> function unstable(flag::Bool)
           if flag
               return 1
           else
               return 1.0
           end
       end
unstable (generic function with 1 method)
```

Es gibt entweder ein `Int` oder ein [`Float64`](@ref), abhängig vom Wert seines Arguments. Da Julia den Rückgabetyp dieser Funktion zur Compile-Zeit nicht vorhersagen kann, muss jede Berechnung, die sie verwendet, in der Lage sein, mit Werten beider Typen umzugehen, was es schwierig macht, schnellen Maschinencode zu erzeugen.

### [Why does Julia give a `DomainError` for certain seemingly-sensible operations?](@id faq-domain-errors)

Bestimmte Operationen ergeben mathematisch Sinn, führen jedoch zu Fehlern:

```jldoctest
julia> sqrt(-2.0)
ERROR: DomainError with -2.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Dieses Verhalten ist eine unangenehme Folge der Anforderung an die Typstabilität. Im Fall von [`sqrt`](@ref) möchten die meisten Benutzer, dass `sqrt(2.0)` eine reelle Zahl zurückgibt, und wären unzufrieden, wenn es die komplexe Zahl `1.4142135623730951 + 0.0im` produzieren würde. Man könnte die `4d61726b646f776e2e436f64652822222c2022737172742229_40726566`-Funktion so schreiben, dass sie nur bei Übergabe einer negativen Zahl zu einer komplexwertigen Ausgabe wechselt (was `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` in einigen anderen Sprachen tut), aber dann wäre das Ergebnis nicht [type-stable](@ref man-type-stability) und die `4d61726b646f776e2e436f64652822222c2022737172742229_40726566`-Funktion hätte eine schlechte Leistung.

In diesen und anderen Fällen können Sie das gewünschte Ergebnis erzielen, indem Sie einen *Eingabetyp* wählen, der Ihre Bereitschaft signalisiert, einen *Ausgabetyp* zu akzeptieren, in dem das Ergebnis dargestellt werden kann:

```jldoctest
julia> sqrt(-2.0+0im)
0.0 + 1.4142135623730951im
```

### How can I constrain or compute type parameters?

Die Parameter eines [parametric type](@ref Parametric-Types) können entweder Typ- oder Bitwerte halten, und der Typ selbst wählt aus, wie er diese Parameter nutzt. Zum Beispiel wird `Array{Float64, 2}` durch den Typ `Float64` parametrisiert, um seinen Elementtyp auszudrücken, und den ganzzahligen Wert `2`, um seine Anzahl der Dimensionen auszudrücken. Wenn Sie Ihren eigenen parametrischen Typ definieren, können Sie Untertyp-Beschränkungen verwenden, um zu erklären, dass ein bestimmter Parameter ein Untertyp ([`<:`](@ref)) eines bestimmten abstrakten Typs oder eines vorherigen Typparameters sein muss. Es gibt jedoch keine spezielle Syntax, um zu erklären, dass ein Parameter ein *Wert* eines bestimmten Typs sein muss — das heißt, Sie können nicht direkt erklären, dass ein dimensionalitätsähnlicher Parameter [`isa`](@ref) `Int` innerhalb der `struct`-Definition ist, zum Beispiel. Ebenso können Sie keine Berechnungen (einschließlich einfacher Dinge wie Addition oder Subtraktion) mit Typparametern durchführen. Stattdessen können diese Arten von Einschränkungen und Beziehungen durch zusätzliche Typparameter ausgedrückt werden, die innerhalb des Typs [constructors](@ref man-constructors) berechnet und durchgesetzt werden.

Als Beispiel, betrachten Sie

```julia
struct ConstrainedType{T,N,N+1} # NOTE: INVALID SYNTAX
    A::Array{T,N}
    B::Array{T,N+1}
end
```

wo der Benutzer durchsetzen möchte, dass der dritte Typ-Parameter immer der zweite plus eins ist. Dies kann mit einem expliziten Typ-Parameter implementiert werden, der von einem [inner constructor method](@ref man-inner-constructor-methods) überprüft wird (wo er mit anderen Überprüfungen kombiniert werden kann):

```julia
struct ConstrainedType{T,N,M}
    A::Array{T,N}
    B::Array{T,M}
    function ConstrainedType(A::Array{T,N}, B::Array{T,M}) where {T,N,M}
        N + 1 == M || throw(ArgumentError("second argument should have one more axis" ))
        new{T,N,M}(A, B)
    end
end
```

Diese Überprüfung ist normalerweise *kostenlos*, da der Compiler die Überprüfung auf gültige konkrete Typen auslassen kann. Wenn das zweite Argument ebenfalls berechnet wird, kann es vorteilhaft sein, einen [outer constructor method](@ref man-outer-constructor-methods) bereitzustellen, der diese Berechnung durchführt:

```julia
ConstrainedType(A) = ConstrainedType(A, compute_B(A))
```

### [Why does Julia use native machine integer arithmetic?](@id faq-integer-arithmetic)

Julia verwendet Maschinenarithmetik für Ganzzahlberechnungen. Das bedeutet, dass der Bereich der `Int`-Werte begrenzt ist und an beiden Enden umschlägt, sodass das Addieren, Subtrahieren und Multiplizieren von Ganzzahlen zu Überläufen oder Unterläufen führen kann, was anfangs zu einigen Ergebnissen führen kann, die beunruhigend sind:

```jldoctest
julia> x = typemax(Int)
9223372036854775807

julia> y = x+1
-9223372036854775808

julia> z = -y
-9223372036854775808

julia> 2*z
0
```

Offensichtlich weicht dies stark von der Art und Weise ab, wie mathematische Ganzzahlen sich verhalten, und man könnte denken, dass es weniger ideal ist, dies einem Benutzer in einer Hochsprache zu offenbaren. Für numerische Arbeiten, bei denen Effizienz und Transparenz von größter Bedeutung sind, sind die Alternativen jedoch schlechter.

Eine Alternative, die in Betracht gezogen werden könnte, wäre, jede ganzzahlige Operation auf Überlauf zu überprüfen und die Ergebnisse auf größere Ganzzahltypen wie [`Int128`](@ref) oder [`BigInt`](@ref) im Falle eines Überlaufs zu befördern. Leider führt dies zu erheblichen Overhead bei jeder ganzzahligen Operation (denken Sie an das Inkrementieren eines Schleifenzählers) – es erfordert das Ausgeben von Code, um zur Laufzeit Überlaufprüfungen nach arithmetischen Anweisungen durchzuführen und Verzweigungen zu handhaben, um potenzielle Überläufe zu behandeln. Schlimmer noch, dies würde jede Berechnung, die Ganzzahlen betrifft, typ-instabil machen. Wie bereits erwähnt, [type-stability is crucial](@ref man-type-stability) für die effektive Generierung von effizientem Code. Wenn Sie sich nicht auf die Ergebnisse von ganzzahligen Operationen verlassen können, die Ganzzahlen sind, ist es unmöglich, schnellen, einfachen Code zu generieren, wie es C- und Fortran-Compiler tun.

Eine Variation dieses Ansatzes, die das Erscheinungsbild von Typinstabilität vermeidet, besteht darin, die `Int` und [`BigInt`](@ref) Typen in einen einzigen hybriden Ganzzahltyp zu fusionieren, der intern die Darstellung ändert, wenn ein Ergebnis nicht mehr in die Größe einer Maschinen-Ganzzahl passt. Während dies oberflächlich Typinstabilität auf der Ebene des Julia-Codes vermeidet, kehrt es das Problem nur unter den Teppich, indem es all die gleichen Schwierigkeiten auf den C-Code überträgt, der diesen hybriden Ganzzahltyp implementiert. Dieser Ansatz *kann* funktionieren und kann in vielen Fällen sogar recht schnell sein, hat jedoch mehrere Nachteile. Ein Problem ist, dass die In-Memory-Darstellung von Ganzzahlen und Arrays von Ganzzahlen nicht mehr mit der natürlichen Darstellung übereinstimmt, die von C, Fortran und anderen Sprachen mit nativen Maschinen-Ganzzahlen verwendet wird. Um also mit diesen Sprachen zu interagieren, müssten wir letztendlich ohnehin native Ganzzahltypen einführen. Jede unbegrenzte Darstellung von Ganzzahlen kann keine feste Anzahl von Bits haben und kann daher nicht inline in einem Array mit festen Slots gespeichert werden – große Ganzzahlwerte erfordern immer separate, heap-zugewiesene Speicher. Und natürlich gibt es, egal wie clever eine hybride Ganzzahlimplementierung ist, immer Leistungstraps – Situationen, in denen die Leistung unerwartet abnimmt. Komplexe Darstellung, mangelnde Interoperabilität mit C und Fortran, die Unfähigkeit, Ganzzahlarrays ohne zusätzlichen Heap-Speicher darzustellen, und unvorhersehbare Leistungsmerkmale machen selbst die cleversten hybriden Ganzzahlimplementierungen zu einer schlechten Wahl für hochleistungsfähige numerische Arbeiten.

Eine Alternative zur Verwendung von hybriden Ganzzahlen oder der Förderung zu BigInts ist die Verwendung von saturierenden Ganzzahlarithmetik, bei der das Hinzufügen zum größten Ganzzahlwert ihn unverändert lässt und ebenso das Subtrahieren vom kleinsten Ganzzahlwert. Genau das macht Matlab™:

```
>> int64(9223372036854775807)

ans =

  9223372036854775807

>> int64(9223372036854775807) + 1

ans =

  9223372036854775807

>> int64(-9223372036854775808)

ans =

 -9223372036854775808

>> int64(-9223372036854775808) - 1

ans =

 -9223372036854775808
```

Auf den ersten Blick scheint dies vernünftig genug, da 9223372036854775807 viel näher an 9223372036854775808 ist als -9223372036854775808 und Ganzzahlen immer noch in einer festen Größe auf eine natürliche Weise dargestellt werden, die mit C und Fortran kompatibel ist. Saturierte Ganzzahl-Arithmetik ist jedoch tief problematisch. Das erste und offensichtlichste Problem ist, dass dies nicht der Art und Weise entspricht, wie die Ganzzahl-Arithmetik von Maschinen funktioniert, sodass die Implementierung gesättigter Operationen erfordert, dass nach jeder Maschinen-Ganzzahloperation Anweisungen ausgegeben werden, um auf Unterlauf oder Überlauf zu überprüfen und das Ergebnis durch [`typemin(Int)`](@ref) oder [`typemax(Int)`](@ref) zu ersetzen, je nach Bedarf. Dies allein erweitert jede Ganzzahloperation von einer einzigen, schnellen Anweisung auf ein halbes Dutzend Anweisungen, wahrscheinlich einschließlich Verzweigungen. Autsch. Aber es wird schlimmer – die saturierte Ganzzahl-Arithmetik ist nicht assoziativ. Betrachten Sie diese Matlab-Berechnung:

```
>> n = int64(2)^62
4611686018427387904

>> n + (n - 1)
9223372036854775807

>> (n + n) - 1
9223372036854775806
```

Dies erschwert das Schreiben vieler grundlegender Ganzzahl-Algorithmen, da viele gängige Techniken davon abhängen, dass die Maschinenaddition mit Überlauf *assoziativ* ist. Betrachten Sie das Finden des Mittelpunkts zwischen den Ganzzahlwerten `lo` und `hi` in Julia mit dem Ausdruck `(lo + hi) >>> 1`:

```jldoctest
julia> n = 2^62
4611686018427387904

julia> (n + 2n) >>> 1
6917529027641081856
```

Siehst du? Kein Problem. Das ist der richtige Mittelpunkt zwischen 2^62 und 2^63, trotz der Tatsache, dass `n + 2n` -4611686018427387904 ist. Versuch es jetzt in Matlab:

```
>> (n + 2*n)/2

ans =

  4611686018427387904
```

Oops. Das Hinzufügen eines `>>>` Operators zu Matlab würde nicht helfen, da die Sättigung, die auftritt, wenn `n` und `2n` addiert werden, bereits die Informationen zerstört hat, die notwendig sind, um den korrekten Mittelpunkt zu berechnen.

Nicht nur ist der Mangel an Assoziativität bedauerlich für Programmierer, die sich nicht darauf verlassen können, um Techniken wie diese anzuwenden, sondern er vereitelt auch fast alles, was Compiler tun könnten, um die Ganzzahl-Arithmetik zu optimieren. Zum Beispiel, da Julia-Ganzzahlen normale Maschinen-Ganzzahl-Arithmetik verwenden, ist LLVM frei, einfache kleine Funktionen wie `f(k) = 5k-1` aggressiv zu optimieren. Der Maschinen-Code für diese Funktion ist einfach dieser:

```julia-repl
julia> code_native(f, Tuple{Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 1
  leaq  -1(%rdi,%rdi,4), %rax
  popq  %rbp
  retq
  nopl  (%rax,%rax)
```

Der eigentliche Körper der Funktion ist eine einzelne `leaq`-Anweisung, die die ganzzahlige Multiplikation und Addition auf einmal berechnet. Dies ist noch vorteilhafter, wenn `f` in eine andere Funktion inline eingefügt wird:

```julia-repl
julia> function g(k, n)
           for i = 1:n
               k = f(k)
           end
           return k
       end
g (generic function with 1 methods)

julia> code_native(g, Tuple{Int,Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 2
  testq %rsi, %rsi
  jle L26
  nopl  (%rax)
Source line: 3
L16:
  leaq  -1(%rdi,%rdi,4), %rdi
Source line: 2
  decq  %rsi
  jne L16
Source line: 5
L26:
  movq  %rdi, %rax
  popq  %rbp
  retq
  nop
```

Da der Aufruf von `f` inline gesetzt wird, besteht der Schleifenrumpf nur aus einer einzigen `leaq`-Anweisung. Betrachten wir als Nächstes, was passiert, wenn wir die Anzahl der Schleifeniterationen festlegen:

```julia-repl
julia> function g(k)
           for i = 1:10
               k = f(k)
           end
           return k
       end
g (generic function with 2 methods)

julia> code_native(g,(Int,))
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 3
  imulq $9765625, %rdi, %rax    # imm = 0x9502F9
  addq  $-2441406, %rax         # imm = 0xFFDABF42
Source line: 5
  popq  %rbp
  retq
  nopw  %cs:(%rax,%rax)
```

Weil der Compiler weiß, dass die Addition und Multiplikation von Ganzzahlen assoziativ sind und dass die Multiplikation über die Addition verteilt – was bei saturierender Arithmetik nicht der Fall ist – kann er die gesamte Schleife auf nur eine Multiplikation und eine Addition optimieren. Die saturierte Arithmetik macht diese Art der Optimierung vollständig zunichte, da Assoziativität und Distributivität in jeder Schleifeniteration fehlschlagen können, was zu unterschiedlichen Ergebnissen führt, je nachdem, in welcher Iteration der Fehler auftritt. Der Compiler kann die Schleife entrollen, aber er kann mehrere Operationen nicht algebraisch in weniger äquivalente Operationen reduzieren.

Die vernünftigste Alternative zur stillen Überlaufbehandlung bei Ganzzahl-Arithmetik besteht darin, überall überprüfte Arithmetik zu verwenden, die Fehler auslöst, wenn Additionen, Subtraktionen und Multiplikationen überlaufen und Werte erzeugen, die nicht wertkorrekt sind. In diesem [blog post](https://danluu.com/integer-overflow/) analysiert Dan Luu dies und stellt fest, dass dieser Ansatz, an sich trivial in den Kosten, in der Praxis aufgrund der Tatsache, dass Compiler (LLVM und GCC) die hinzugefügten Überlaufprüfungen nicht elegant optimieren, erhebliche Kosten verursacht. Wenn sich dies in Zukunft verbessert, könnten wir in Erwägung ziehen, in Julia standardmäßig auf überprüfte Ganzzahl-Arithmetik umzuschalten, aber im Moment müssen wir mit der Möglichkeit eines Überlaufs leben.

In der Zwischenzeit können überlauf-sichere Ganzzahloperationen durch die Verwendung externer Bibliotheken wie [SaferIntegers.jl](https://github.com/JeffreySarnoff/SaferIntegers.jl) erreicht werden. Beachten Sie, dass die Verwendung dieser Bibliotheken, wie bereits erwähnt, die Ausführungszeit des Codes, der die überprüften Ganzzahltypen verwendet, erheblich erhöht. Für eine begrenzte Nutzung ist dies jedoch weit weniger problematisch, als wenn es für alle Ganzzahloperationen verwendet würde. Sie können den Status der Diskussion [here](https://github.com/JuliaLang/julia/issues/855) verfolgen.

### What are the possible causes of an `UndefVarError` during remote execution?

Wie der Fehler besagt, ist eine unmittelbare Ursache für einen `UndefVarError` auf einem Remote-Knoten, dass eine Bindung mit diesem Namen nicht existiert. Lassen Sie uns einige der möglichen Ursachen untersuchen.

```julia-repl
julia> module Foo
           foo() = remotecall_fetch(x->x, 2, "Hello")
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `Foo` not defined in `Main`
Stacktrace:
[...]
```

Der Closure `x->x` trägt eine Referenz auf `Foo`, und da `Foo` auf Knoten 2 nicht verfügbar ist, wird ein `UndefVarError` ausgelöst.

Globale Variablen unter Modulen außer `Main` werden nicht als Wert an den Remote-Knoten serialisiert. Es wird nur ein Verweis gesendet. Funktionen, die globale Bindungen erstellen (außer unter `Main`), können später einen `UndefVarError` auslösen.

```julia-repl
julia> @everywhere module Foo
           function foo()
               global gvar = "Hello"
               remotecall_fetch(()->gvar, 2)
           end
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `gvar` not defined in `Main.Foo`
Stacktrace:
[...]
```

Im obigen Beispiel definierte `@everywhere module Foo` `Foo` auf allen Knoten. Der Aufruf von `Foo.foo()` erzeugte jedoch eine neue globale Bindung `gvar` auf dem lokalen Knoten, die auf Knoten 2 nicht gefunden wurde, was zu einem `UndefVarError`-Fehler führte.

Beachten Sie, dass dies nicht für Globals gilt, die im Modul `Main` erstellt wurden. Globals im Modul `Main` werden serialisiert und neue Bindungen, die im `Main` auf dem Remote-Knoten erstellt werden.

```julia-repl
julia> gvar_self = "Node1"
"Node1"

julia> remotecall_fetch(()->gvar_self, 2)
"Node1"

julia> remotecall_fetch(varinfo, 2)
name          size summary
––––––––– –––––––– –––––––
Base               Module
Core               Module
Main               Module
gvar_self 13 bytes String
```

Dies gilt nicht für `function`- oder `struct`-Deklarationen. Anonyme Funktionen, die an globale Variablen gebunden sind, werden jedoch serialisiert, wie unten zu sehen ist.

```julia-repl
julia> bar() = 1
bar (generic function with 1 method)

julia> remotecall_fetch(bar, 2)
ERROR: On worker 2:
UndefVarError: `#bar` not defined in `Main`
[...]

julia> anon_bar  = ()->1
(::#21) (generic function with 1 method)

julia> remotecall_fetch(anon_bar, 2)
1
```

## Troubleshooting "method not matched": parametric type invariance and `MethodError`s

### Why doesn't it work to declare `foo(bar::Vector{Real}) = 42` and then call `foo([1])`?

Wie Sie sehen werden, wenn Sie dies ausprobieren, ist das Ergebnis ein `MethodError`:

```jldoctest
julia> foo(x::Vector{Real}) = 42
foo (generic function with 1 method)

julia> foo([1])
ERROR: MethodError: no method matching foo(::Vector{Int64})
The function `foo` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  foo(!Matched::Vector{Real})
   @ Main none:1

Stacktrace:
[...]
```

Das liegt daran, dass `Vector{Real}` kein Supertyp von `Vector{Int}` ist! Sie können dieses Problem mit etwas wie `foo(bar::Vector{T}) where {T<:Real}` lösen (oder der Kurzform `foo(bar::Vector{<:Real})`, wenn der statische Parameter `T` im Funktionskörper nicht benötigt wird). Das `T` ist ein Platzhalter: Sie geben zuerst an, dass es ein Subtyp von Real sein muss, und dann geben Sie an, dass die Funktion einen Vektor mit Elementen dieses Typs entgegennimmt.

Dieses gleiche Problem gilt für jeden zusammengesetzten Typ `Comp`, nicht nur für `Vector`. Wenn `Comp` einen Parameter vom Typ `Y` deklariert hat, dann ist ein anderer Typ `Comp2` mit einem Parameter vom Typ `X<:Y` kein Subtyp von `Comp`. Dies ist Typ-Invarianz (im Gegensatz dazu ist Tuple typ-kovariant in seinen Parametern). Siehe [Parametric Composite Types](@ref man-parametric-composite-types) für weitere Erklärungen dazu.

### Why does Julia use `*` for string concatenation? Why not `+` or something else?

Die [main argument](@ref man-concatenation) gegen `+` ist, dass die Zeichenkettenverkettung nicht kommutativ ist, während `+` allgemein als kommutativer Operator verwendet wird. Während die Julia-Community anerkennt, dass andere Sprachen unterschiedliche Operatoren verwenden und `*` für einige Benutzer möglicherweise ungewohnt ist, kommuniziert es bestimmte algebraische Eigenschaften.

Beachten Sie, dass Sie auch `string(...)` verwenden können, um Zeichenfolgen (und andere in Zeichenfolgen umgewandelte Werte) zu verketten; ähnlich kann `repeat` anstelle von `^` verwendet werden, um Zeichenfolgen zu wiederholen. Die [interpolation syntax](@ref string-interpolation) ist ebenfalls nützlich zum Erstellen von Zeichenfolgen.

## Packages and Modules

### What is the difference between "using" and "import"?

Es gibt mehrere Unterschiede zwischen `using` und `import` (siehe die [Modules section](https://docs.julialang.org/en/v1/manual/modules/#modules)), aber es gibt einen wichtigen Unterschied, der auf den ersten Blick nicht intuitiv erscheinen mag, und auf der Oberfläche (d.h. syntaxtechnisch) mag er sehr geringfügig erscheinen. Beim Laden von Modulen mit `using` müssen Sie `function Foo.bar(...` sagen, um die Funktion `bar` des Moduls `Foo` mit einer neuen Methode zu erweitern, aber mit `import Foo.bar` müssen Sie nur `function bar(...` sagen, und es erweitert automatisch die Funktion `bar` des Moduls `Foo`.

Der Grund, warum dies wichtig genug ist, um eine separate Syntax zu erhalten, ist, dass Sie nicht versehentlich eine Funktion erweitern möchten, von der Sie nicht wussten, dass sie existiert, da dies leicht einen Fehler verursachen könnte. Dies geschieht am wahrscheinlichsten mit einer Methode, die einen gemeinsamen Typ wie einen String oder eine Ganzzahl akzeptiert, da sowohl Sie als auch das andere Modul eine Methode definieren könnten, um einen solchen gemeinsamen Typ zu behandeln. Wenn Sie `import` verwenden, ersetzen Sie die Implementierung von `bar(s::AbstractString)` des anderen Moduls durch Ihre neue Implementierung, die leicht etwas völlig anderes tun könnte (und alle/viele zukünftigen Verwendungen der anderen Funktionen im Modul Foo, die von der Aufruf von bar abhängen, brechen könnte).

## Nothingness and missing values

### [How does "null", "nothingness" or "missingness" work in Julia?](@id faq-nothing)

Im Gegensatz zu vielen Sprachen (zum Beispiel C und Java) können Julia-Objekte standardmäßig nicht "null" sein. Wenn eine Referenz (Variable, Objektfeld oder Array-Element) nicht initialisiert ist, führt der Zugriff darauf sofort zu einem Fehler. Diese Situation kann mit den Funktionen [`isdefined`](@ref) oder [`isassigned`](@ref Base.isassigned) erkannt werden.

Einige Funktionen werden nur wegen ihrer Nebenwirkungen verwendet und müssen keinen Wert zurückgeben. In diesen Fällen ist es üblich, den Wert `nothing` zurückzugeben, der einfach ein Singleton-Objekt des Typs `Nothing` ist. Dies ist ein gewöhnlicher Typ ohne Felder; es gibt nichts Besonderes daran, außer dieser Konvention und dass die REPL nichts dafür ausgibt. Einige Sprachkonstrukte, die ansonsten keinen Wert hätten, ergeben ebenfalls `nothing`, zum Beispiel `if false; end`.

Für Situationen, in denen ein Wert `x` vom Typ `T` nur manchmal existiert, kann der Typ `Union{T, Nothing}` für Funktionsargumente, Objektfelder und Array-Elementtypen verwendet werden, als Äquivalent zu [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type) in anderen Sprachen. Wenn der Wert selbst `nothing` sein kann (insbesondere, wenn `T` `Any` ist), ist der Typ `Union{Some{T}, Nothing}` geeigneter, da `x == nothing` dann das Fehlen eines Wertes anzeigt und `x == Some(nothing)` die Anwesenheit eines Wertes, der gleich `nothing` ist, anzeigt. Die Funktion [`something`](@ref) ermöglicht das Entpacken von `Some`-Objekten und die Verwendung eines Standardwerts anstelle von `nothing`-Argumenten. Beachten Sie, dass der Compiler in der Lage ist, effizienten Code zu generieren, wenn er mit `Union{T, Nothing}`-Argumenten oder -Feldern arbeitet.

Um fehlende Daten im statistischen Sinne darzustellen (`NA` in R oder `NULL` in SQL), verwenden Sie das [`missing`](@ref) Objekt. Weitere Einzelheiten finden Sie im Abschnitt [`Missing Values`](@ref missing).

In einigen Sprachen wird das leere Tupel (`()`) als die kanonische Form des Nichts betrachtet. In Julia sollte es jedoch am besten als ein reguläres Tupel angesehen werden, das zufällig null Werte enthält.

Der leere (oder "untere") Typ, geschrieben als `Union{}` (ein leerer Unionstyp), ist ein Typ ohne Werte und ohne Subtypen (außer sich selbst). In der Regel müssen Sie diesen Typ nicht verwenden.

## Memory

### Why does `x += y` allocate memory when `x` and `y` are arrays?

In Julia wird `x += y` während des Niedrigens durch `x = x + y` ersetzt. Für Arrays hat dies zur Folge, dass anstelle des Speicherns des Ergebnisses am selben Speicherort wie `x` ein neues Array zur Speicherung des Ergebnisses zugewiesen wird. Wenn Sie `x` lieber mutieren möchten, verwenden Sie `x .+= y`, um jedes Element einzeln zu aktualisieren.

Während dieses Verhalten einige überraschen mag, ist die Wahl absichtlich. Der Hauptgrund ist die Anwesenheit von unveränderlichen Objekten in Julia, die ihren Wert nach der Erstellung nicht ändern können. Tatsächlich ist eine Zahl ein unveränderliches Objekt; die Anweisungen `x = 5; x += 1` ändern nicht die Bedeutung von `5`, sie ändern den Wert, der an `x` gebunden ist. Bei einem Unveränderlichen ist die einzige Möglichkeit, den Wert zu ändern, ihn neu zuzuweisen.

Um ein wenig weiter zu verstärken, betrachten Sie die folgende Funktion:

```julia
function power_by_squaring(x, n::Int)
    ispow2(n) || error("This implementation only works for powers of 2")
    while n >= 2
        x *= x
        n >>= 1
    end
    x
end
```

Nach einem Aufruf wie `x = 5; y = power_by_squaring(x, 4)` würden Sie das erwartete Ergebnis erhalten: `x == 5 && y == 625`. Angenommen, `*=`, wenn es mit Matrizen verwendet wird, würde nun die linke Seite mutieren. Es gäbe zwei Probleme:

  * Für allgemeine quadratische Matrizen kann `A = A*B` nicht ohne temporären Speicher implementiert werden: `A[1,1]` wird berechnet und auf der linken Seite gespeichert, bevor Sie es auf der rechten Seite vollständig verwendet haben.
  * Angenommen, Sie wären bereit, einen temporären Speicher für die Berechnung zuzuweisen (was den Großteil des Sinns, `*=` in-place zu verwenden, beseitigen würde); wenn Sie die Änderbarkeit von `x` nutzen würden, würde diese Funktion sich unterschiedlich für veränderliche und unveränderliche Eingaben verhalten. Insbesondere hätten Sie für unveränderliches `x` nach dem Aufruf (im Allgemeinen) `y != x`, aber für veränderliches `x` hätten Sie `y == x`.

Weil die Unterstützung von generischer Programmierung als wichtiger erachtet wird als potenzielle Leistungsoptimierungen, die auf andere Weise erreicht werden können (z. B. durch Broadcasting oder explizite Schleifen), funktionieren Operatoren wie `+=` und `*=` durch das Binden neuer Werte.

## [Asynchronous IO and concurrent synchronous writes](@id faq-async-io)

### Why do concurrent writes to the same stream result in inter-mixed output?

Während die Streaming-I/O-API synchron ist, ist die zugrunde liegende Implementierung vollständig asynchron.

Bitte fügen Sie den Markdown-Inhalt oder den Text hinzu, den Sie übersetzen möchten.

```jldoctest
julia> @sync for i in 1:3
           @async write(stdout, string(i), " Foo ", " Bar ")
       end
123 Foo  Foo  Foo  Bar  Bar  Bar
```

Dies geschieht, weil der `write`-Aufruf synchron ist, das Schreiben jedes Arguments jedoch anderen Aufgaben nachgibt, während auf den Abschluss dieses Teils der E/A gewartet wird.

`print` und `println` "sperren" den Stream während eines Aufrufs. Folglich führt das Ändern von `write` zu `println` im obigen Beispiel zu:

```jldoctest
julia> @sync for i in 1:3
           @async println(stdout, string(i), " Foo ", " Bar ")
       end
1 Foo  Bar
2 Foo  Bar
3 Foo  Bar
```

Sie können Ihre Schreibvorgänge mit einem `ReentrantLock` wie folgt sperren:

```jldoctest
julia> l = ReentrantLock();

julia> @sync for i in 1:3
           @async begin
               lock(l)
               try
                   write(stdout, string(i), " Foo ", " Bar ")
               finally
                   unlock(l)
               end
           end
       end
1 Foo  Bar 2 Foo  Bar 3 Foo  Bar
```

## Arrays

### [What are the differences between zero-dimensional arrays and scalars?](@id faq-array-0dim)

Nulldimensionale Arrays sind Arrays der Form `Array{T,0}`. Sie verhalten sich ähnlich wie Skalare, aber es gibt wichtige Unterschiede. Sie verdienen eine besondere Erwähnung, da sie einen Sonderfall darstellen, der im Hinblick auf die generische Definition von Arrays logisch ist, aber anfangs etwas unintuitiv sein könnte. Die folgende Zeile definiert ein nulldimensionales Array:

```
julia> A = zeros()
0-dimensional Array{Float64,0}:
0.0
```

In diesem Beispiel ist `A` ein veränderlicher Container, der ein Element enthält, das mit `A[] = 1.0` gesetzt und mit `A[]` abgerufen werden kann. Alle nulldimensionalen Arrays haben die gleiche Größe (`size(A) == ()`) und Länge (`length(A) == 1`). Insbesondere sind nulldimensionale Arrays nicht leer. Wenn Sie dies unintuitiv finden, hier sind einige Ideen, die helfen könnten, Julias Definition zu verstehen.

  * Nulldimensionale Arrays sind der "Punkt" zur "Linie" des Vektors und der "Ebene" der Matrix. So wie eine Linie keine Fläche hat (aber dennoch eine Menge von Dingen repräsentiert), hat ein Punkt keine Länge oder Dimensionen (repräsentiert aber dennoch eine Sache).
  * Wir definieren `prod(())` als 1, und die Gesamtanzahl der Elemente in einem Array ist das Produkt der Größe. Die Größe eines null-dimensionalen Arrays ist `()`, und daher ist seine Länge `1`.
  * Nulldimensionale Arrays haben von Natur aus keine Dimensionen, in die Sie indizieren können – sie sind einfach `A[]`. Wir können dieselbe Regel "nachfolgend eins" für sie anwenden wie für alle anderen Array-Dimensionalitäten, sodass Sie sie tatsächlich als `A[1]`, `A[1,1]` usw. indizieren können; siehe [Omitted and extra indices](@ref).

Es ist auch wichtig, die Unterschiede zu gewöhnlichen Skalaren zu verstehen. Skalare sind keine veränderbaren Container (auch wenn sie durchlaufbar sind und Dinge wie `length`, `getindex` definieren, *z.B.* `1[] == 1`). Insbesondere ist es ein Fehler, den Wert eines als Skalar definierten `x = 0.0` zu ändern, indem man `x[] = 1.0` versucht. Ein Skalar `x` kann über `fill(x)` in ein nulldimensionales Array umgewandelt werden, das es enthält, und umgekehrt kann ein nulldimensionales Array `a` in den enthaltenen Skalar über `a[]` umgewandelt werden. Ein weiterer Unterschied besteht darin, dass ein Skalar an linearen Algebraoperationen wie `2 * rand(2,2)` teilnehmen kann, aber die analoge Operation mit einem nulldimensionalen Array `fill(2) * rand(2,2)` ein Fehler ist.

### Why are my Julia benchmarks for linear algebra operations different from other languages?

Sie werden feststellen, dass einfache Benchmarks von Bausteinen der linearen Algebra wie

```julia
using BenchmarkTools
A = randn(1000, 1000)
B = randn(1000, 1000)
@btime $A \ $B
@btime $A * $B
```

kann sich von anderen Sprachen wie Matlab oder R unterscheiden.

Da solche Operationen sehr dünne Wrapper über die relevanten BLAS-Funktionen sind, ist der Grund für die Diskrepanz sehr wahrscheinlich

1. die BLAS-Bibliothek, die jede Sprache verwendet,
2. die Anzahl der gleichzeitigen Threads.

Julia kompiliert und verwendet eine eigene Kopie von OpenBLAS, wobei die Threads derzeit auf `8` (oder die Anzahl Ihrer Kerne) begrenzt sind.

Die Modifizierung der OpenBLAS-Einstellungen oder das Kompilieren von Julia mit einer anderen BLAS-Bibliothek, z. B. [Intel MKL](https://software.intel.com/en-us/mkl), kann Leistungsverbesserungen bieten. Sie können [MKL.jl](https://github.com/JuliaComputing/MKL.jl) verwenden, ein Paket, das Julias lineare Algebra dazu bringt, Intel MKL BLAS und LAPACK anstelle von OpenBLAS zu verwenden, oder im Diskussionsforum nach Vorschlägen suchen, wie Sie dies manuell einrichten können. Beachten Sie, dass Intel MKL nicht mit Julia gebündelt werden kann, da es nicht Open Source ist.

## Computing cluster

### How do I manage precompilation caches in distributed file systems?

Wenn Sie Julia in Hochleistungsrechenzentren (HPC) mit gemeinsamen Dateisystemen verwenden, wird empfohlen, ein gemeinsames Depot (über die [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) Umgebungsvariable) zu verwenden. Seit Julia v1.10 koordinieren mehrere Julia-Prozesse auf funktional ähnlichen Arbeitern, die dasselbe Depot verwenden, über pidfile-Locks, um nur in einem Prozess Aufwand für die Vorcompilierung zu betreiben, während die anderen warten. Der Vorcompilierungsprozess zeigt an, wann der Prozess vorcompiliert oder auf einen anderen wartet, der vorcompiliert. Wenn nicht interaktiv, erfolgen die Nachrichten über `@debug`.

Allerdings ist die Cache-Ablehnung seit v1.9 aufgrund des Cachens von Binärcode strenger, und die Benutzer müssen möglicherweise die Umgebungsvariable [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) entsprechend festlegen, um einen einzelnen Cache zu erhalten, der in der gesamten HPC-Umgebung verwendbar ist.

## Julia Releases

### Do I want to use the Stable, LTS, or nightly version of Julia?

Die stabile Version von Julia ist die neueste veröffentlichte Version von Julia, die die Version ist, die die meisten Menschen verwenden möchten. Sie verfügt über die neuesten Funktionen, einschließlich verbesserter Leistung. Die stabile Version von Julia wird gemäß [SemVer](https://semver.org/) als v1.x.y versioniert. Eine neue Minor-Version von Julia, die einer neuen stabilen Version entspricht, wird ungefähr alle 4-5 Monate nach ein paar Wochen Testphase als Release-Kandidat veröffentlicht. Im Gegensatz zur LTS-Version erhält die stabile Version normalerweise keine Bugfixes, nachdem eine andere stabile Version von Julia veröffentlicht wurde. Das Upgrade auf die nächste stabile Version wird jedoch immer möglich sein, da jede Version von Julia v1.x weiterhin Code aus früheren Versionen ausführen kann.

Sie bevorzugen möglicherweise die LTS (Long Term Support) Version von Julia, wenn Sie nach einer sehr stabilen Codebasis suchen. Die aktuelle LTS-Version von Julia ist gemäß SemVer als v1.6.x versioniert; dieser Branch wird weiterhin Bugfixes erhalten, bis ein neuer LTS-Branch ausgewählt wird, zu diesem Zeitpunkt wird die v1.6.x-Serie keine regelmäßigen Bugfixes mehr erhalten und alle bis auf die konservativsten Benutzer werden geraten, auf die neue LTS-Version umzusteigen. Als Paketentwickler möchten Sie möglicherweise für die LTS-Version entwickeln, um die Anzahl der Benutzer zu maximieren, die Ihr Paket verwenden können. Laut SemVer wird Code, der für v1.0 geschrieben wurde, weiterhin mit allen zukünftigen LTS- und Stable-Versionen funktionieren. Im Allgemeinen kann man, selbst wenn man auf die LTS abzielt, Code in der neuesten Stable-Version entwickeln und ausführen, um von der verbesserten Leistung zu profitieren; solange man es vermeidet, neue Funktionen (wie hinzugefügte Bibliotheksfunktionen oder neue Methoden) zu verwenden.

Sie bevorzugen möglicherweise die nächtliche Version von Julia, wenn Sie die neuesten Updates der Sprache nutzen möchten und es Ihnen nichts ausmacht, wenn die heute verfügbare Version gelegentlich nicht funktioniert. Wie der Name schon sagt, werden die Veröffentlichungen der nächtlichen Version ungefähr jede Nacht (abhängig von der Stabilität der Build-Infrastruktur) vorgenommen. Im Allgemeinen sind nächtliche Versionen recht sicher zu verwenden – Ihr Code wird nicht in Flammen aufgehen. Es kann jedoch gelegentlich Rückschritte oder Probleme geben, die erst bei gründlicheren Tests vor der Veröffentlichung entdeckt werden. Sie möchten möglicherweise gegen die nächtliche Version testen, um sicherzustellen, dass solche Rückschritte, die Ihren Anwendungsfall betreffen, vor einer Veröffentlichung erkannt werden.

Schließlich können Sie auch in Betracht ziehen, Julia selbst aus dem Quellcode zu erstellen. Diese Option richtet sich hauptsächlich an Personen, die mit der Befehlszeile vertraut sind oder daran interessiert sind, zu lernen. Wenn dies auf Sie zutrifft, könnten Sie auch daran interessiert sein, unseren [guidelines for contributing](https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md) zu lesen.

Links zu jedem dieser Download-Typen finden Sie auf der Download-Seite unter [https://julialang.org/downloads/](https://julialang.org/downloads/). Beachten Sie, dass nicht alle Versionen von Julia für alle Plattformen verfügbar sind.

### How can I transfer the list of installed packages after updating my version of Julia?

Jede Minor-Version von Julia hat ihre eigene Standard [environment](https://docs.julialang.org/en/v1/manual/code-loading/#Environments-1). Daher sind nach der Installation einer neuen Minor-Version von Julia die Pakete, die Sie mit der vorherigen Minor-Version hinzugefügt haben, standardmäßig nicht verfügbar. Die Umgebung für eine bestimmte Julia-Version wird durch die Dateien `Project.toml` und `Manifest.toml` in einem Ordner definiert, der der Versionsnummer in `.julia/environments/` entspricht, zum Beispiel `.julia/environments/v1.3`.

Wenn Sie eine neue Minor-Version von Julia installieren, sagen wir `1.4`, und im Standardumfeld dieselben Pakete wie in einer vorherigen Version (z. B. `1.3`) verwenden möchten, können Sie den Inhalt der Datei `Project.toml` aus dem `1.3`-Ordner in den `1.4`-Ordner kopieren. Geben Sie dann in einer Sitzung der neuen Julia-Version den "Paketverwaltungsmodus" ein, indem Sie die Taste `]` drücken, und führen Sie den Befehl [`instantiate`](https://julialang.github.io/Pkg.jl/v1/api/#Pkg.instantiate) aus.

Dieser Vorgang wird eine Menge von kompatiblen Paketen aus der kopierten Datei ermitteln, die mit der Ziel-Julia-Version kompatibel sind, und sie installieren oder aktualisieren, wenn dies geeignet ist. Wenn Sie nicht nur die Menge der Pakete, sondern auch die Versionen, die Sie in der vorherigen Julia-Version verwendet haben, reproduzieren möchten, sollten Sie auch die Datei `Manifest.toml` kopieren, bevor Sie den Pkg-Befehl `instantiate` ausführen. Beachten Sie jedoch, dass Pakete Kompatibilitätsbeschränkungen definieren können, die durch die Änderung der Julia-Version beeinflusst werden können, sodass die genaue Menge der Versionen, die Sie in `1.3` hatten, möglicherweise nicht für `1.4` funktioniert.
