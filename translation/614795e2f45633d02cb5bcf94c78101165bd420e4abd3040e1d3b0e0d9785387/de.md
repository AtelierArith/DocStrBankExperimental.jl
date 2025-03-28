# [Documentation](@id man-documentation)

## Accessing Documentation

Die Dokumentation kann im REPL oder unter [IJulia](https://github.com/JuliaLang/IJulia.jl) aufgerufen werden, indem Sie `?` gefolgt vom Namen einer Funktion oder Makro eingeben und `Enter` drücken. Zum Beispiel,

```julia
?cos
?@time
?r""
```

wird die Dokumentation für die jeweilige Funktion, das Makro oder das String-Makro anzeigen. Die meisten Julia-Umgebungen bieten eine Möglichkeit, direkt auf die Dokumentation zuzugreifen:

  * [VS Code](https://www.julia-vscode.org/) zeigt die Dokumentation an, wenn Sie über einen Funktionsnamen fahren. Sie können auch das Julia-Panel in der Seitenleiste verwenden, um nach Dokumentation zu suchen.
  * In [Pluto](https://github.com/fonsp/Pluto.jl), öffnen Sie das "Live Docs"-Panel in der unteren rechten Ecke.
  * In [Juno](https://junolab.org) zeigt `Strg-J, Strg-D` die Dokumentation für das Objekt unter dem Cursor an.

`Docs.hasdoc(module, name)::Bool` gibt an, ob ein Name eine Dokumentation hat. `Docs.undocumented_names(module; all)` gibt die undokumentierten Namen in einem Modul zurück.

## Writing Documentation

Julia ermöglicht es Paketentwicklern und -benutzern, Funktionen, Typen und andere Objekte einfach über ein integriertes Dokumentationssystem zu dokumentieren.

Die grundlegende Syntax ist einfach: Jeder String, der direkt vor einem Objekt (Funktion, Makro, Typ oder Instanz) erscheint, wird als Dokumentation dafür interpretiert (diese werden *Docstrings* genannt). Beachten Sie, dass keine Leerzeilen oder Kommentare zwischen einem Docstring und dem dokumentierten Objekt stehen dürfen. Hier ist ein einfaches Beispiel:

```julia
"Tell whether there are too foo items in the array."
foo(xs::Array) = ...
```

Dokumentation wird als [Markdown](https://en.wikipedia.org/wiki/Markdown) interpretiert, sodass Sie Einrückungen und Code-Umrandungen verwenden können, um Codebeispiele vom Text zu trennen. Technisch gesehen kann jedes Objekt mit jedem anderen als Metadaten verknüpft werden; Markdown ist zufällig das Standardformat, aber man kann auch andere String-Makros erstellen und diese ebenso an das `@doc`-Makro übergeben.

!!! note
    Markdown-Unterstützung ist in der `Markdown`-Standardbibliothek implementiert, und für eine vollständige Liste der unterstützten Syntax siehe die [documentation](@ref markdown_stdlib).


Hier ist ein komplexeres Beispiel, das weiterhin Markdown verwendet:

````julia
"""
    bar(x[, y])

Compute the Bar index between `x` and `y`.

If `y` is unspecified, compute the Bar index between all pairs of columns of `x`.

# Examples
```julia-repl
julia> bar([1, 2], [1, 2])
1
```
"""
function bar(x, y) ...
````

Wie im obigen Beispiel empfohlen, empfehlen wir, einige einfache Konventionen beim Schreiben von Dokumentationen zu befolgen:

1. Always show the signature of a function at the top of the documentation, with a four-space indent so that it is printed as Julia code.

    Dies kann identisch mit der Signatur im Julia-Code sein (wie `mean(x::AbstractArray)`), oder in einer vereinfachten Form. Optionale Argumente sollten, wenn möglich, mit ihren Standardwerten dargestellt werden (d.h. `f(x, y=1)`), wobei die tatsächliche Julia-Syntax befolgt wird. Optionale Argumente, die keinen Standardwert haben, sollten in Klammern gesetzt werden (d.h. `f(x[, y])` und `f(x[, y[, z]])`). Eine alternative Lösung besteht darin, mehrere Zeilen zu verwenden: eine ohne optionale Argumente, die anderen mit ihnen. Diese Lösung kann auch verwendet werden, um mehrere verwandte Methoden einer bestimmten Funktion zu dokumentieren. Wenn eine Funktion viele Schlüsselwortargumente akzeptiert, sollte nur ein `<keyword arguments>` Platzhalter in der Signatur enthalten sein (d.h. `f(x; <keyword arguments>)`), und die vollständige Liste sollte unter einem `# Arguments` Abschnitt angegeben werden (siehe Punkt 4 unten).
2. Fügen Sie nach dem vereinfachten Signaturblock einen einzelnen einzeiligen Satz hinzu, der beschreibt, was die Funktion tut oder was das Objekt darstellt. Falls erforderlich, geben Sie weitere Details in einem zweiten Absatz nach einem Leerzeichen an.

    Die einzeilige Beschreibung sollte die Imperativform verwenden ("Mach dies", "Gib das zurück") anstelle der dritten Person (schreibe nicht "Gibt die Länge zurück..."), wenn Funktionen dokumentiert werden. Sie sollte mit einem Punkt enden. Wenn die Bedeutung einer Funktion nicht leicht zusammengefasst werden kann, könnte es vorteilhaft sein, sie in separate zusammensetzbare Teile zu unterteilen (dies sollte jedoch nicht als absolute Anforderung für jeden einzelnen Fall angesehen werden).
3. Vermeiden Sie Wiederholungen.

    Da der Funktionsname durch die Signatur gegeben ist, ist es nicht notwendig, die Dokumentation mit "Die Funktion `bar`..." zu beginnen: Kommen Sie direkt zur Sache. Ebenso ist es überflüssig, die Typen der Argumente zu erwähnen, wenn sie in der Signatur angegeben sind.
4. Nur eine Argumentliste bereitstellen, wenn es wirklich notwendig ist.

    Für einfache Funktionen ist es oft klarer, die Rolle der Argumente direkt in der Beschreibung des Zwecks der Funktion zu erwähnen. Eine Argumentenliste würde nur Informationen wiederholen, die bereits an anderer Stelle bereitgestellt wurden. Das Bereitstellen einer Argumentenliste kann jedoch eine gute Idee für komplexe Funktionen mit vielen Argumenten (insbesondere Schlüsselwortargumenten) sein. In diesem Fall fügen Sie sie nach der allgemeinen Beschreibung der Funktion unter einer `# Argumente`-Überschrift ein, mit einem `-` Aufzählungszeichen für jedes Argument. Die Liste sollte die Typen und Standardwerte (sofern vorhanden) der Argumente erwähnen:

    ```julia
    """
    ...
    # Arguments
    - `n::Integer`: the number of elements to compute.
    - `dim::Integer=1`: the dimensions along which to perform the computation.
    ...
    """
    ```
5. Geben Sie Hinweise zu verwandten Funktionen.

    Manchmal gibt es Funktionen mit verwandter Funktionalität. Um die Auffindbarkeit zu erhöhen, geben Sie bitte eine kurze Liste dieser in einem `Siehe auch`-Absatz an.

    ```
    See also [`bar!`](@ref), [`baz`](@ref), [`baaz`](@ref).
    ```
6. Include any code examples in an `# Examples` section.

    Beispiele sollten, wann immer möglich, als *doctests* geschrieben werden. Ein *doctest* ist ein eingezäunter Codeblock (siehe [Code blocks](@ref)), der mit ````` ```jldoctest````` beginnt und beliebig viele `julia>`-Eingabeaufforderungen zusammen mit Eingaben und erwarteten Ausgaben enthält, die die Julia REPL nachahmen.

    !!! note
        Doctests sind aktiviert durch [`Documenter.jl`](https://github.com/JuliaDocs/Documenter.jl). Für detailliertere Dokumentation siehe Documenter's [manual](https://juliadocs.github.io/Documenter.jl/).


    Zum Beispiel wird in der folgenden Docstring eine Variable `a` definiert und das erwartete Ergebnis, wie es in einer Julia REPL angezeigt wird, erscheint danach:

    ````julia
    """
    Some nice documentation here.

    # Examples
    ```jldoctest
    julia> a = [1 2; 3 4]
    2×2 Array{Int64,2}:
     1  2
     3  4
    ```
    """
    ````

    !!! warning
        Das Aufrufen von `rand` und anderen RNG-bezogenen Funktionen sollte in Doctests vermieden werden, da sie in verschiedenen Julia-Sitzungen keine konsistenten Ausgaben erzeugen. Wenn Sie einige Funktionen zur Zufallszahlengenerierung demonstrieren möchten, ist eine Möglichkeit, Ihr eigenes RNG-Objekt explizit zu erstellen und zu initialisieren (siehe [`Random`](@ref Random-Numbers)) und es an die Funktionen zu übergeben, die Sie testen.

        Betriebssystem-Wortgröße ([`Int32`](@ref) oder [`Int64`](@ref)) sowie Unterschiede im Pfadtrennzeichen (`/` oder `\`) werden ebenfalls die Reproduzierbarkeit einiger Doctests beeinflussen.

        Beachten Sie, dass Leerzeichen in Ihrem Doctest von Bedeutung sind! Der Doctest schlägt fehl, wenn Sie die Ausgabe der schönen Druckausgabe eines Arrays falsch ausrichten, zum Beispiel.


    Sie können dann `make -C doc doctest=true` ausführen, um alle Doctests im Julia-Handbuch und in der API-Dokumentation auszuführen, was sicherstellt, dass Ihr Beispiel funktioniert.

    Um anzuzeigen, dass das Ausgabeergebnis abgeschnitten ist, können Sie `[...]` an der Stelle schreiben, an der die Überprüfung gestoppt werden soll. Dies ist nützlich, um einen Stacktrace (der nicht permanente Verweise auf Zeilen von Julia-Code enthält) zu verbergen, wenn der Doctest zeigt, dass eine Ausnahme ausgelöst wird, zum Beispiel:

    ````julia
    ```jldoctest
    julia> div(1, 0)
    ERROR: DivideError: integer division error
    [...]
    ```
    ````

    Beispiele, die nicht testbar sind, sollten innerhalb von eingezäunten Codeblöcken geschrieben werden, die mit ````` ```julia````` beginnen, damit sie in der generierten Dokumentation korrekt hervorgehoben werden.

    !!! tip
        Wo immer möglich, sollten Beispiele **selbstständig** und **ausführbar** sein, damit die Leser sie ausprobieren können, ohne irgendwelche Abhängigkeiten einfügen zu müssen.
7. Verwenden Sie Backticks, um Code und Gleichungen zu kennzeichnen.

    Julia-Identifikatoren und Codeausschnitte sollten immer zwischen Backticks ``` ` ``` erscheinen, um die Hervorhebung zu ermöglichen. Gleichungen im LaTeX-Syntax können zwischen doppelten Backticks ``` `` ```. Unicode-Zeichen sollten anstelle ihrer LaTeX-Escape-Sequenzen verwendet werden, d.h. ``` ``α = 1`` ``` anstelle von ``` ``\\alpha = 1`` ```.
8. Place the starting and ending `"""` characters on lines by themselves.

    Das heißt, schreibe:

    ```julia
    """
    ...

    ...
    """
    f(x, y) = ...
    ```

    statt:

    ```julia
    """...

    ..."""
    f(x, y) = ...
    ```

    Das macht es klarer, wo Docstrings beginnen und enden.
9. Respektieren Sie das Zeilenlängenlimit, das im umgebenden Code verwendet wird.

    Docstrings werden mit denselben Werkzeugen wie Code bearbeitet. Daher sollten die gleichen Konventionen gelten. Es wird empfohlen, dass die Zeilen höchstens 92 Zeichen breit sind.
10. Provide information allowing custom types to implement the function in an `# Implementation` section. These implementation details are intended for developers rather than users, explaining e.g. which functions should be overridden and which functions automatically use appropriate fallbacks. Such details are best kept separate from the main description of the function's behavior.
11. Für lange Docstrings sollten Sie in Betracht ziehen, die Dokumentation mit einer `# Erweiterte Hilfe`-Überschrift zu unterteilen. Der typische Hilfemodus zeigt nur das Material über der Überschrift an; Sie können auf die vollständige Hilfe zugreifen, indem Sie ein '?' am Anfang des Ausdrucks hinzufügen (d.h. "??foo" anstelle von "?foo").

## Functions & Methods

Funktionen in Julia können mehrere Implementierungen haben, die als Methoden bekannt sind. Während es eine gute Praxis ist, dass generische Funktionen einen einzigen Zweck haben, erlaubt Julia es, Methoden bei Bedarf einzeln zu dokumentieren. Im Allgemeinen sollte nur die allgemeinste Methode dokumentiert werden, oder sogar die Funktion selbst (d.h. das Objekt, das ohne Methoden mit `function bar end` erstellt wurde). Spezifische Methoden sollten nur dokumentiert werden, wenn sich ihr Verhalten von den allgemeineren unterscheidet. In jedem Fall sollten sie die Informationen, die anderswo bereitgestellt werden, nicht wiederholen. Zum Beispiel:

```julia
"""
    *(x, y, z...)

Multiplication operator. `x * y * z *...` calls this function with multiple
arguments, i.e. `*(x, y, z...)`.
"""
function *(x, y, z...)
    # ... [implementation sold separately] ...
end

"""
    *(x::AbstractString, y::AbstractString, z::AbstractString...)

When applied to strings, concatenates them.
"""
function *(x::AbstractString, y::AbstractString, z::AbstractString...)
    # ... [insert secret sauce here] ...
end

help?> *
search: * .*

  *(x, y, z...)

  Multiplication operator. x * y * z *... calls this function with multiple
  arguments, i.e. *(x,y,z...).

  *(x::AbstractString, y::AbstractString, z::AbstractString...)

  When applied to strings, concatenates them.
```

Beim Abrufen der Dokumentation für eine generische Funktion wird die Metadaten für jede Methode mit der Funktion `catdoc` verknüpft, die natürlich für benutzerdefinierte Typen überschrieben werden kann.

## Advanced Usage

Das `@doc`-Makro verknüpft sein erstes Argument mit seinem zweiten in einem modul-spezifischen Wörterbuch namens `META`.

Um das Schreiben von Dokumentationen zu erleichtern, behandelt der Parser den Makronamen `@doc` speziell: Wenn ein Aufruf von `@doc` ein Argument hat, aber ein anderer Ausdruck nach einem Zeilenumbruch erscheint, wird dieser zusätzliche Ausdruck als Argument an das Makro angehängt. Daher wird die folgende Syntax als ein 2-Argumente-Aufruf von `@doc` interpretiert:

```julia
@doc raw"""
...
"""
f(x) = x
```

Dies ermöglicht die Verwendung von Ausdrücken, die keine normalen String-Literale sind (wie das `raw""` String-Makro), als Docstring.

Wenn sie zum Abrufen von Dokumentationen verwendet wird, sucht das `@doc`-Makro (oder ebenso die `doc`-Funktion) in allen `META`-Dictionaries nach Metadaten, die für das gegebene Objekt relevant sind, und gibt sie zurück. Das zurückgegebene Objekt (zum Beispiel ein Markdown-Inhalt) wird standardmäßig intelligent angezeigt. Dieses Design erleichtert auch die programmgesteuerte Verwendung des Dokumentsystems; zum Beispiel, um Dokumentationen zwischen verschiedenen Versionen einer Funktion wiederzuverwenden:

```julia
@doc "..." foo!
@doc (@doc foo!) foo
```

Oder zur Verwendung mit Julias Metaprogrammierungsfunktionalität:

```julia
for (f, op) in ((:add, :+), (:subtract, :-), (:multiply, :*), (:divide, :/))
    @eval begin
        $f(a, b) = $op(a, b)
    end
end
@doc "`add(a, b)` adds `a` and `b` together" add
@doc "`subtract(a, b)` subtracts `b` from `a`" subtract
```

Dokumentation in nicht-top-level Blöcken, wie `begin`, `if`, `for`, `let` und inneren Konstruktoren, sollte ebenfalls über `@doc` in das Dokumentationssystem aufgenommen werden. Zum Beispiel:

```julia
if condition()
    @doc "..."
    f(x) = x
end
```

wird Dokumentation zu `f(x)` hinzugefügt, wenn `condition()` `true` ist. Beachten Sie, dass die Dokumentation von `f(x)` auch dann erhalten bleibt, wenn `f(x)` am Ende eines Blocks aus dem Gültigkeitsbereich fällt.

Es ist möglich, Metaprogrammierung zu nutzen, um die Erstellung von Dokumentationen zu unterstützen. Bei der Verwendung von String-Interpolation innerhalb des Docstrings müssen Sie ein zusätzliches `$` verwenden, wie mit `$($name)` gezeigt:

```julia
for func in (:day, :dayofmonth)
    name = string(func)
    @eval begin
        @doc """
            $($name)(dt::TimeType) -> Int64

        The day of month of a `Date` or `DateTime` as an `Int64`.
        """ $func(dt::Dates.TimeType)
    end
end
```

### Dynamic documentation

Manchmal hängt die geeignete Dokumentation für eine Instanz eines Typs von den Feldwerten dieser Instanz ab, und nicht nur vom Typ selbst. In diesen Fällen können Sie eine Methode zu `Docs.getdoc` für Ihren benutzerdefinierten Typ hinzufügen, die die Dokumentation auf Basis jeder Instanz zurückgibt. Zum Beispiel,

```julia
struct MyType
    value::Int
end

Docs.getdoc(t::MyType) = "Documentation for MyType with value $(t.value)"

x = MyType(1)
y = MyType(2)
```

`?x` zeigt "Dokumentation für MyType mit Wert 1" an, während `?y` "Dokumentation für MyType mit Wert 2" anzeigt.

## Syntax Guide

Dieser Leitfaden bietet einen umfassenden Überblick darüber, wie man Dokumentation an alle Julia-Syntaxkonstrukte anfügt, für die das Bereitstellen von Dokumentation möglich ist.

In den folgenden Beispielen wird `"..."` verwendet, um eine beliebige Docstring zu veranschaulichen.

### `$` and `\` characters

Die `$`- und `\`-Zeichen werden auch in Docstrings als String-Interpolation oder Beginn einer Escape-Sequenz interpretiert. Die `raw""`-String-Makro zusammen mit dem `@doc`-Makro kann verwendet werden, um das Entkommen dieser Zeichen zu vermeiden. Dies ist nützlich, wenn die Docstrings LaTeX oder Julia-Quellcodebeispiele enthalten, die Interpolation beinhalten:

````julia
@doc raw"""
```math
\LaTeX
```
"""
function f end
````

### Functions and Methods

```julia
"..."
function f end

"..."
f
```

Fügt der Funktion `f` einen Docstring `"..."` hinzu. Die erste Version ist die bevorzugte Syntax, jedoch sind beide gleichwertig.

```julia
"..."
f(x) = x

"..."
function f(x)
    return x
end

"..."
f(x)
```

Fügt die Docstring `"..."` zur Methode `f(::Any)` hinzu.

```julia
"..."
f(x, y = 1) = x + y
```

Fügt Docstrings `"..."` zu zwei `Methoden` hinzu, nämlich `f(::Any)` und `f(::Any, ::Any)`.

### Macros

```julia
"..."
macro m(x) end
```

Fügt den Docstring `"..."` zur `@m(::Any)` Makrodefinition hinzu.

```julia
"..."
:(@m1)

"..."
macro m2 end
```

Fügt den Docstring `"..."` zu den Makros mit den Namen `@m1` und `@m2` hinzu.

### Types

```
"..."
abstract type T1 end

"..."
mutable struct T2
    ...
end

"..."
struct T3
    ...
end
```

Fügt den Docstring `"..."` zu den Typen `T1`, `T2` und `T3` hinzu.

```
"..."
T1

"..."
T2

"..."
T3
```

Fügt den Docstring `"..."` zu den Typen `T1`, `T2` und `T3` hinzu. Die vorherige Version ist die bevorzugte Syntax, jedoch sind beide gleichwertig.

```julia
"..."
struct T
    "x"
    x
    "y"
    y

    @doc "Inner constructor"
    function T()
        new(...)
    end
end
```

Fügt den Docstring `"..."` zum Typ `T`, `"x"` zum Feld `T.x`, `"y"` zum Feld `T.y` und `"Inner constructor"` zum inneren Konstruktor `T()` hinzu. Gilt auch für `mutable struct`-Typen.

### Modules

```julia
"..."
module M end

module M

"..."
M

end
```

Fügt den Docstring `"..."` zum `Modul` `M` hinzu. Das Hinzufügen des Docstrings über dem `Modul` ist die bevorzugte Syntax, jedoch sind beide gleichwertig.

```julia
"..."
baremodule M
# ...
end

baremodule M

import Base: @doc

"..."
f(x) = x

end
```

Die Dokumentation eines `baremodule` durch das Platzieren eines Docstrings über dem Ausdruck importiert automatisch `@doc` in das Modul. Diese Importe müssen manuell durchgeführt werden, wenn der Modulexpress nicht dokumentiert ist.

### Global Variables

```julia
"..."
const a = 1

"..."
b = 2

"..."
global c = 3
```

Fügt die Docstring `"..."` zu den `Binding`s `a`, `b` und `c` hinzu.

`Binding`s werden verwendet, um eine Referenz auf ein bestimmtes `Symbol` in einem `Module` zu speichern, ohne den referenzierten Wert selbst zu speichern.

!!! note
    Wenn eine `const`-Definition nur verwendet wird, um ein Alias für eine andere Definition zu erstellen, wie es bei der Funktion `div` und ihrem Alias `÷` in `Base` der Fall ist, dokumentieren Sie das Alias nicht und dokumentieren Sie stattdessen die tatsächliche Funktion.

    Wenn das Alias dokumentiert ist und nicht die echte Definition, wird das Docsystem (Modus `?`) die Docstring, die dem Alias angehängt ist, nicht zurückgeben, wenn nach der echten Definition gesucht wird.

    Zum Beispiel solltest du schreiben

    ```julia
    "..."
    f(x) = x + 1
    const alias = f
    ```

    stattdessen

    ```julia
    f(x) = x + 1
    "..."
    const alias = f
    ```


```julia
"..."
sym
```

Fügt einen Docstring `"..."` zum Wert hinzu, der mit `sym` verknüpft ist. Es wird jedoch bevorzugt, dass `sym` dort dokumentiert wird, wo es definiert ist.

### Multiple Objects

```julia
"..."
a, b
```

Fügt den Docstring `"..."` zu `a` und `b` hinzu, die jeweils ein dokumentierbarer Ausdruck sein sollten. Diese Syntax ist äquivalent zu

```julia
"..."
a

"..."
b
```

Jede Anzahl von Ausdrücken kann auf diese Weise dokumentiert werden. Diese Syntax kann nützlich sein, wenn zwei Funktionen miteinander verwandt sind, wie nicht-mutierende und mutierende Versionen `f` und `f!`.

### Macro-generated code

```julia
"..."
@m expression
```

Fügt den Docstring `"..."` zu dem Ausdruck hinzu, der durch die Erweiterung von `@m expression` generiert wird. Dies ermöglicht es, dass Ausdrücke, die mit `@inline`, `@noinline`, `@generated` oder einem anderen Makro dekoriert sind, auf die gleiche Weise dokumentiert werden wie undekorierte Ausdrücke.

Macro-Autoren sollten beachten, dass nur Makros, die einen einzelnen Ausdruck generieren, automatisch Docstrings unterstützen. Wenn ein Makro einen Block zurückgibt, der mehrere Unterausdrücke enthält, muss der Unterausdruck, der dokumentiert werden soll, mit dem [`@__doc__`](@ref Core.@__doc__)-Makro gekennzeichnet werden.

Das [`@enum`](@ref) Makro nutzt `@__doc__`, um die Dokumentation von [`Enum`](@ref) zu ermöglichen. Die Untersuchung seiner Definition sollte als Beispiel dienen, wie `@__doc__` korrekt verwendet wird.

```@docs
Core.@__doc__
```
