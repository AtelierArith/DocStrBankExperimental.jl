# Julia Functions

Dieses Dokument erklärt, wie Funktionen, Methodendefinitionen und Methodentabellen funktionieren.

## Method Tables

Jede Funktion in Julia ist eine generische Funktion. Eine generische Funktion ist konzeptionell eine einzelne Funktion, besteht jedoch aus vielen Definitionen oder Methoden. Die Methoden einer generischen Funktion werden in einer Methodentabelle gespeichert. Methodentabellen (Typ `MethodTable`) sind mit `TypeName`s verbunden. Ein `TypeName` beschreibt eine Familie von parametrisierten Typen. Zum Beispiel teilen sich `Complex{Float32}` und `Complex{Float64}` dasselbe `Complex`-Typnamenobjekt.

Alle Objekte in Julia sind potenziell aufrufbar, da jedes Objekt einen Typ hat, der wiederum einen `TypeName` hat.

## [Function calls](@id Function-calls)

Gegeben dem Aufruf `f(x, y)` werden die folgenden Schritte durchgeführt: Zuerst wird die zu verwendende Methodentabelle als `typeof(f).name.mt` abgerufen. Zweitens wird ein Argument-Tupeltyp gebildet, `Tuple{typeof(f), typeof(x), typeof(y)}`. Beachten Sie, dass der Typ der Funktion selbst das erste Element ist. Dies liegt daran, dass der Typ Parameter haben könnte und daher an der Dispatch teilnehmen muss. Dieser Tupeltyp wird in der Methodentabelle nachgeschlagen.

Dieser Dispatch-Prozess wird von `jl_apply_generic` durchgeführt, das zwei Argumente entgegennimmt: einen Zeiger auf ein Array der Werte `f`, `x` und `y` sowie die Anzahl der Werte (in diesem Fall 3).

Im gesamten System gibt es zwei Arten von APIs, die Funktionen und Argumentlisten verarbeiten: solche, die die Funktion und die Argumente separat akzeptieren, und solche, die eine einzelne Argumentstruktur akzeptieren. Bei der ersten Art von API enthält der Teil "Argumente" *keine* Informationen über die Funktion, da diese separat übergeben wird. Bei der zweiten Art von API ist die Funktion das erste Element der Argumentstruktur.

Zum Beispiel akzeptiert die folgende Funktion zum Ausführen eines Aufrufs nur einen `args`-Zeiger, sodass das erste Element des args-Arrays die aufzurufende Funktion sein wird:

```c
jl_value_t *jl_apply(jl_value_t **args, uint32_t nargs)
```

Dieser Einstiegspunkt für dieselbe Funktionalität akzeptiert die Funktion separat, sodass das `args`-Array die Funktion nicht enthält:

```c
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs);
```

## Adding methods

Angesichts des oben beschriebenen Dispatch-Prozesses ist konzeptionell alles, was benötigt wird, um eine neue Methode hinzuzufügen, (1) ein Tupeltyp und (2) Code für den Körper der Methode. `jl_method_def` implementiert diesen Vorgang. `jl_method_table_for` wird aufgerufen, um die relevante Methodentabelle aus dem zu extrahieren, was der Typ des ersten Arguments wäre. Dies ist viel komplizierter als das entsprechende Verfahren während des Dispatchs, da der Argumenttupeltyp abstrakt sein könnte. Zum Beispiel können wir definieren:

```julia
(::Union{Foo{Int},Foo{Int8}})(x) = 0
```

was funktioniert, da alle möglichen Übereinstimmungsverfahren zur gleichen Methodentabelle gehören würden.

## Creating generic functions

Da jedes Objekt aufrufbar ist, ist nichts Besonderes erforderlich, um eine generische Funktion zu erstellen. Daher erstellt `jl_new_generic_function` einfach einen neuen Singleton (0 Größe) Untertyp von `Function` und gibt dessen Instanz zurück. Eine Funktion kann einen mnemonischen "Anzeigenamen" haben, der in Debug-Informationen und beim Drucken von Objekten verwendet wird. Zum Beispiel ist der Name von `Base.sin` `sin`. Üblicherweise hat der erstellte *Typ* denselben Namen wie die Funktion, mit einem `#` davor. Daher ist `typeof(sin)` `Base.#sin`.

## Closures

Ein Closure ist einfach ein aufrufbares Objekt mit Feldnamen, die den erfassten Variablen entsprechen. Zum Beispiel der folgende Code:

```julia
function adder(x)
    return y->x+y
end
```

wird auf (ungefähr) gesenkt:

```julia
struct ##1{T}
    x::T
end

(_::##1)(y) = _.x + y

function adder(x)
    return ##1(x)
end
```

## Constructors

Ein Konstruktoraufruf ist einfach ein Aufruf eines Typs. Die Methodentabelle für `Type` enthält alle Konstruktordefinitionen. Alle Untertypen von `Type` (`Type`, `UnionAll`, `Union` und `DataType`) teilen sich derzeit über eine spezielle Vereinbarung eine Methodentabelle.

## Builtins

Die "builtin" Funktionen, die im `Core` Modul definiert sind, sind:

```@eval
function lines(words)
    io = IOBuffer()
    n = 0
    for w in words
        if n+length(w) > 80
            print(io, '\n', w)
            n = length(w)
        elseif n == 0
            print(io, w);
            n += length(w)
        else
            print(io, ' ', w);
            n += length(w)+1
        end
    end
    String(take!(io))
end
import Markdown
[string(n) for n in names(Core;all=true)
    if getfield(Core,n) isa Core.Builtin && nameof(getfield(Core,n)) === n] |>
    lines |>
    s ->  "```\n$s\n```" |>
    Markdown.parse
```

Dies sind alles Singleton-Objekte, deren Typen Untertypen von `Builtin` sind, das ein Untertyp von `Function` ist. Ihr Zweck ist es, Einstiegspunkte zur Laufzeit bereitzustellen, die das "jlcall"-Aufrufkonventionsschema verwenden:

```c
jl_value_t *(jl_value_t*, jl_value_t**, uint32_t)
```

Die Methodentabellen der Builtins sind leer. Stattdessen haben sie einen einzigen Auffang-Methoden-Cache-Eintrag (`Tuple{Vararg{Any}}`), dessen jlcall fptr auf die richtige Funktion zeigt. Das ist eine Art Hack, funktioniert aber ziemlich gut.

## Keyword arguments

Keyword-Argumente funktionieren, indem Methoden zur Funktion kwcall hinzugefügt werden. Diese Funktion ist normalerweise der "Keyword-Argument-Sorter" oder "Keyword-Sorter", der dann den inneren Körper der Funktion (anonym definiert) aufruft. Jede Definition in der Funktion kwsorter hat die gleichen Argumente wie eine Definition in der normalen Methodentabelle, mit der Ausnahme, dass ein einzelnes `NamedTuple`-Argument vorangestellt ist, das die Namen und Werte der übergebenen Keyword-Argumente angibt. Die Aufgabe des kwsorters besteht darin, Keyword-Argumente basierend auf ihrem Namen in ihre kanonischen Positionen zu verschieben, sowie benötigte Standardwertausdrücke auszuwerten und zu ersetzen. Das Ergebnis ist eine normale Liste von Positionsargumenten, die dann an eine weitere vom Compiler generierte Funktion übergeben wird.

Der einfachste Weg, den Prozess zu verstehen, besteht darin, sich anzusehen, wie eine Methode mit Schlüsselwortargumenten definiert wird. Der Code:

```julia
function circle(center, radius; color = black, fill::Bool = true, options...)
    # draw
end
```

tatsächlich produziert es *drei* Methodendefinitionen. Die erste ist eine Funktion, die alle Argumente (einschließlich der Schlüsselwortargumente) als Positionsargumente akzeptiert und den Code für den Methodenrumpf enthält. Sie hat einen automatisch generierten Namen:

```julia
function #circle#1(color, fill::Bool, options, circle, center, radius)
    # draw
end
```

Die zweite Methode ist eine gewöhnliche Definition für die ursprüngliche `circle`-Funktion, die den Fall behandelt, in dem keine Schlüsselwortargumente übergeben werden:

```julia
function circle(center, radius)
    #circle#1(black, true, pairs(NamedTuple()), circle, center, radius)
end
```

Dies leitet einfach an die erste Methode weiter und übergibt die Standardwerte. `pairs` wird auf das benannte Tupel der Restargumente angewendet, um die Iteration über Schlüssel-Wert-Paare bereitzustellen. Beachten Sie, dass dieses Argument fehlt, wenn die Methode keine Rest-Keyword-Argumente akzeptiert.

Schließlich gibt es die Definition des kwsorters:

```
function (::Core.kwftype(typeof(circle)))(kws, circle, center, radius)
    if haskey(kws, :color)
        color = kws.color
    else
        color = black
    end
    # etc.

    # put remaining kwargs in `options`
    options = structdiff(kws, NamedTuple{(:color, :fill)})

    # if the method doesn't accept rest keywords, throw an error
    # unless `options` is empty

    #circle#1(color, fill, pairs(options), circle, center, radius)
end
```

Die Funktion `Core.kwftype(t)` erstellt das Feld `t.name.mt.kwsorter` (falls es noch nicht erstellt wurde) und gibt den Typ dieser Funktion zurück.

Dieses Design hat die Eigenschaft, dass Aufrufstellen, die keine Schlüsselwortargumente verwenden, keine besondere Behandlung erfordern; alles funktioniert, als ob sie überhaupt nicht Teil der Sprache wären. Aufrufstellen, die Schlüsselwortargumente verwenden, werden direkt an den kwsorter der aufgerufenen Funktion weitergeleitet. Zum Beispiel der Aufruf:

```julia
circle((0, 0), 1.0, color = red; other...)
```

wird gesenkt auf:

```julia
kwcall(merge((color = red,), other), circle, (0, 0), 1.0)
```

`kwcall` (auch in `Core`) bezeichnet eine kwcall-Signatur und -Dispatch. Die Schlüsselwort-Splatting-Operation (geschrieben als `other...`) ruft die benannte Tupel-Funktion `merge` auf. Diese Funktion entpackt weiter jedes *Element* von `other` und erwartet, dass jedes davon zwei Werte enthält (ein Symbol und einen Wert). Natürlich ist eine effizientere Implementierung verfügbar, wenn alle gesplatteten Argumente benannte Tupel sind. Beachten Sie, dass die ursprüngliche `circle`-Funktion durchgereicht wird, um Closures zu behandeln.

## [Compiler efficiency issues](@id compiler-efficiency-issues)

Die Generierung eines neuen Typs für jede Funktion hat potenziell schwerwiegende Folgen für den Ressourcenverbrauch des Compilers, wenn sie mit Julias Design "Standardmäßig auf allen Argumenten spezialisieren" kombiniert wird. Tatsächlich litt die ursprüngliche Implementierung dieses Designs unter deutlich längeren Build- und Testzeiten, höherem Speicherverbrauch und einem Systembild, das fast doppelt so groß war wie die Basisversion. In einer naiven Implementierung ist das Problem so gravierend, dass das System nahezu unbenutzbar wird. Mehrere bedeutende Optimierungen waren erforderlich, um das Design praktikabel zu machen.

Das erste Problem ist die übermäßige Spezialisierung von Funktionen für verschiedene Werte von funktionswertigen Argumenten. Viele Funktionen "leiten" einfach ein Argument irgendwohin weiter, z. B. an eine andere Funktion oder an einen Speicherort. Solche Funktionen müssen nicht für jede Closure spezialisiert werden, die übergeben werden könnte. Glücklicherweise ist dieser Fall leicht zu unterscheiden, indem man einfach betrachtet, ob eine Funktion eines ihrer Argumente *aufruft* (d. h. das Argument erscheint irgendwo in "Kopfposition"). Leistungs-kritische höherwertige Funktionen wie `map` rufen sicherlich ihre Argumentfunktion auf und werden daher wie erwartet spezialisiert. Diese Optimierung wird umgesetzt, indem aufgezeichnet wird, welche Argumente während des `analyze-variables`-Durchlaufs im Frontend aufgerufen werden. Wenn `cache_method` ein Argument in der `Function`-Typ-Hierarchie sieht, das an einen Slot übergeben wird, der als `Any` oder `Function` deklariert ist, verhält es sich so, als ob die `@nospecialize`-Annotation angewendet worden wäre. Diese Heuristik scheint in der Praxis äußerst effektiv zu sein.

Das nächste Thema betrifft die Struktur der Hash-Tabellen für Methodencaches. Empirische Studien zeigen, dass die überwiegende Mehrheit der dynamisch dispatchten Aufrufe ein oder zwei Argumente umfasst. Viele dieser Fälle können wiederum gelöst werden, indem nur das erste Argument betrachtet wird. (Nebenbei bemerkt: Befürworter des Single Dispatch wären darüber überhaupt nicht überrascht. Dieses Argument bedeutet jedoch "Multiple Dispatch ist in der Praxis leicht zu optimieren", und dass wir es daher verwenden sollten, *nicht* "wir sollten Single Dispatch verwenden"!) Daher verwendet der Methodencache den Typ des ersten Arguments als seinen Primärschlüssel. Beachten Sie jedoch, dass dies dem *zweiten* Element des Tupeltyps für einen Funktionsaufruf entspricht (das erste Element ist der Typ der Funktion selbst). Typischerweise ist die Typvariation in der Kopfposition extrem gering – in der Tat gehören die meisten Funktionen zu Singleton-Typen ohne Parameter. Dies ist jedoch nicht der Fall für Konstruktoren, bei denen eine einzelne Methodentabelle Konstruktoren für jeden Typ enthält. Daher wird die `Type`-Methodentabelle speziell behandelt, um das *erste* Tupeltyp-Element anstelle des zweiten zu verwenden.

Die Front-End-Generierung erstellt Typdeklarationen für alle Closures. Zunächst wurde dies durch die Generierung normaler Typdeklarationen implementiert. Dies führte jedoch zu einer extrem großen Anzahl von Konstruktoren, von denen alle trivial waren (einfach alle Argumente an [`new`](@ref) weiterzugeben). Da Methoden teilweise geordnet sind, ist das Einfügen all dieser Methoden O(n²), und es gibt einfach zu viele von ihnen, um sie zu behalten. Dies wurde optimiert, indem `struct_type`-Ausdrücke direkt generiert wurden (um die Standardkonstruktor-Generierung zu umgehen) und `new` direkt verwendet wurde, um Closure-Instanzen zu erstellen. Nicht die schönste Lösung, aber man tut, was man tun muss.

Das nächste Problem war das `@test`-Makro, das für jeden Testfall einen 0-Argumente-Closure generierte. Dies ist nicht wirklich notwendig, da jeder Testfall einfach einmal an Ort und Stelle ausgeführt wird. Daher wurde `@test` so modifiziert, dass es sich in einen Try-Catch-Block erweitert, der das Testergebnis (wahr, falsch oder ausgelöste Ausnahme) aufzeichnet und den Test-Suite-Handler darauf aufruft.
