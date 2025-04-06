# [Modules](@id modules)

Module in Julia helfen, den Code in kohärente Einheiten zu organisieren. Sie sind syntaktisch innerhalb von `module NameOfModule ... end` abgegrenzt und haben die folgenden Merkmale:

1. Module sind separate Namensräume, die jeweils einen neuen globalen Geltungsbereich einführen. Dies ist nützlich, da es ermöglicht, denselben Namen für verschiedene Funktionen oder globale Variablen ohne Konflikte zu verwenden, solange sie sich in separaten Modulen befinden.
2. Module haben Einrichtungen für eine detaillierte Namensraumverwaltung: Jeder definiert eine Menge von Namen, die er `export` und als `öffentlich` markiert, und kann Namen aus anderen Modulen mit `using` und `import` importieren (wir erklären diese unten).
3. Module können vorcompiliert werden, um das Laden zu beschleunigen, und können Code für die Laufzeitanpassung enthalten.

Typischerweise werden in größeren Julia-Paketen die Modulcodes in Dateien organisiert, z. B.

```julia
module SomeModule

# export, public, using, import statements are usually here; we discuss these below

include("file1.jl")
include("file2.jl")

end
```

Dateien und Dateinamen stehen größtenteils in keinem Zusammenhang mit Modulen; Module sind nur mit Modulausdrücken verbunden. Man kann mehrere Dateien pro Modul und mehrere Module pro Datei haben. `include` verhält sich so, als ob der Inhalt der Quelldatei im globalen Geltungsbereich des einbindenden Moduls ausgewertet wurde. In diesem Kapitel verwenden wir kurze und vereinfachte Beispiele, daher werden wir `include` nicht verwenden.

Der empfohlene Stil besteht darin, den Körper des Moduls nicht einzurücken, da dies typischerweise dazu führen würde, dass ganze Dateien eingerückt werden. Außerdem ist es üblich, `UpperCamelCase` für Modulenamen zu verwenden (genauso wie für Typen) und die Pluralform zu verwenden, wenn dies zutrifft, insbesondere wenn das Modul einen ähnlich benannten Bezeichner enthält, um Namenskonflikte zu vermeiden. Zum Beispiel,

```julia
module FastThings

struct FastThing
    ...
end

end
```

## [Namespace management](@id namespace-management)

Namespace-Management bezieht sich auf die Funktionen, die die Sprache bietet, um Namen in einem Modul in anderen Modulen verfügbar zu machen. Wir diskutieren die verwandten Konzepte und Funktionen im Folgenden ausführlich.

### Qualified names

Namen für Funktionen, Variablen und Typen im globalen Geltungsbereich wie `sin`, `ARGS` und `UnitRange` gehören immer zu einem Modul, das als *Elternmodul* bezeichnet wird und interaktiv mit [`parentmodule`](@ref) gefunden werden kann, zum Beispiel.

```jldoctest
julia> parentmodule(UnitRange)
Base
```

Man kann diese Namen auch außerhalb ihres übergeordneten Moduls ansprechen, indem man sie mit ihrem Modul prefixiert, z.B. `Base.UnitRange`. Dies wird als *qualifizierter Name* bezeichnet. Das übergeordnete Modul kann über eine Kette von Untermodulen zugänglich sein, wie `Base.Math.sin`, wobei `Base.Math` als *Modulpfad* bezeichnet wird. Aufgrund syntaktischer Mehrdeutigkeiten erfordert die Qualifizierung eines Namens, der nur Symbole enthält, wie einen Operator, das Einfügen eines Doppelpunkts, z.B. `Base.:+`. Eine kleine Anzahl von Operatoren erfordert zusätzlich Klammern, z.B. `Base.:(==)`.

Wenn ein Name qualifiziert ist, dann ist er immer *zugänglich*, und im Falle einer Funktion können auch Methoden hinzugefügt werden, indem der qualifizierte Name als Funktionsname verwendet wird.

Innerhalb eines Moduls kann ein Variablenname "reserviert" werden, ohne ihm einen Wert zuzuweisen, indem er als `global x` deklariert wird. Dies verhindert Namenskonflikte für globale Variablen, die nach der Ladezeit initialisiert werden. Die Syntax `M.x = y` funktioniert nicht, um eine globale Variable in einem anderen Modul zuzuweisen; die globale Zuweisung ist immer modul-lokal.

### Export lists

Namen (die Funktionen, Typen, globalen Variablen und Konstanten betreffen) können mit `export` zur *Exportliste* eines Moduls hinzugefügt werden: Dies sind die Symbole, die importiert werden, wenn `using` das Modul verwendet. Typischerweise befinden sie sich am Anfang oder in der Nähe der Moduldefinition, damit Leser des Quellcodes sie leicht finden können, wie in

```jldoctest module_manual
julia> module NiceStuff
       export nice, DOG
       struct Dog end      # singleton type, not exported
       const DOG = Dog()   # named instance, exported
       nice(x) = "nice $x" # function, exported
       end;

```

aber dies ist nur ein Stilvorschlag — ein Modul kann mehrere `export`-Anweisungen an beliebigen Stellen haben.

Es ist üblich, Namen zu exportieren, die Teil der API (Application Programming Interface) sind. Im obigen Code deutet die Exportliste darauf hin, dass Benutzer `nice` und `DOG` verwenden sollten. Da qualifizierte Namen jedoch immer Bezeichner zugänglich machen, ist dies nur eine Option zur Organisation von APIs: Im Gegensatz zu anderen Sprachen bietet Julia keine Möglichkeiten, die internen Module wirklich zu verbergen.

Außerdem exportieren einige Module überhaupt keine Namen. Dies geschieht normalerweise, wenn sie gängige Wörter wie `derivative` in ihrer API verwenden, die leicht mit den Exportlisten anderer Module in Konflikt geraten könnten. Wir werden unten sehen, wie man Namenskonflikte verwaltet.

Um einen Namen als öffentlich zu kennzeichnen, ohne ihn in den Namensraum der Personen zu exportieren, die `using NiceStuff` aufrufen, kann man `public` anstelle von `export` verwenden. Dies kennzeichnet den/ die öffentlichen Namen als Teil der öffentlichen API, hat jedoch keine Auswirkungen auf den Namensraum. Das Schlüsselwort `public` ist nur in Julia 1.11 und höher verfügbar. Um die Kompatibilität mit Julia 1.10 und älter zu gewährleisten, verwenden Sie das `@compat`-Makro aus dem [Compat](https://github.com/JuliaLang/Compat.jl)-Paket.

### Standalone `using` and `import`

Für interaktive Nutzung ist die gebräuchlichste Methode, ein Modul zu laden, `using ModuleName`. Dies [loads](@ref code-loading) den Code, der mit `ModuleName` verbunden ist, und bringt

1. der Modulname
2. und die Elemente der Exportliste in den umgebenden globalen Namensraum.

Technisch bedeutet die Anweisung `using ModuleName`, dass ein Modul namens `ModuleName` verfügbar sein wird, um Namen nach Bedarf aufzulösen. Wenn eine globale Variable gefunden wird, die in dem aktuellen Modul keine Definition hat, wird das System nach ihr unter den von `ModuleName` exportierten Variablen suchen und sie verwenden, wenn sie dort gefunden wird. Das bedeutet, dass alle Verwendungen dieser globalen Variable im aktuellen Modul auf die Definition dieser Variablen in `ModuleName` aufgelöst werden.

Um ein Modul aus einem Paket zu laden, kann die Anweisung `using ModuleName` verwendet werden. Um ein Modul aus einem lokal definierten Modul zu laden, muss ein Punkt vor dem Modulnamen hinzugefügt werden, wie `using .ModuleName`.

Um mit unserem Beispiel fortzufahren,

```jldoctest module_manual
julia> using .NiceStuff
```

würde den obigen Code laden, wodurch `NiceStuff` (der Modulname), `DOG` und `nice` verfügbar werden. `Dog` steht nicht auf der Exportliste, kann jedoch zugegriffen werden, wenn der Name mit dem Modulpfad qualifiziert wird (der hier nur der Modulname ist) als `NiceStuff.Dog`.

Wichtig ist, dass **`using ModuleName` die einzige Form ist, für die Exportlisten überhaupt von Bedeutung sind**.

Im Gegensatz dazu,

```jldoctest module_manual
julia> import .NiceStuff
```

bringt *nur* den Modulnamen in den Geltungsbereich. Benutzer müssten `NiceStuff.DOG`, `NiceStuff.Dog` und `NiceStuff.nice` verwenden, um auf dessen Inhalte zuzugreifen. In der Regel wird `import ModuleName` in Kontexten verwendet, in denen der Benutzer den Namensraum sauber halten möchte. Wie wir im nächsten Abschnitt sehen werden, ist `import .NiceStuff` gleichbedeutend mit `using .NiceStuff: NiceStuff`.

Sie können mehrere `using`- und `import`-Anweisungen derselben Art in einem durch Kommas getrennten Ausdruck kombinieren, z. B.

```jldoctest module_manual
julia> using LinearAlgebra, Random
```

### `using` and `import` with specific identifiers, and adding methods

Wenn `using ModuleName:` oder `import ModuleName:` von einer durch Kommas getrennten Liste von Namen gefolgt wird, wird das Modul geladen, aber *nur diese spezifischen Namen werden durch die Anweisung in den Namensraum gebracht*. Zum Beispiel,

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG
```

werden die Namen `nice` und `DOG` importiert.

Wichtig ist, dass der Modulname `NiceStuff` *nicht* im Namensraum enthalten sein wird. Wenn Sie ihn zugänglich machen möchten, müssen Sie ihn ausdrücklich auflisten, wie

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG, NiceStuff
```

Wenn zwei oder mehr Pakete/Module einen Namen exportieren und dieser Name in jedem der Pakete nicht dasselbe bezeichnet, und die Pakete über `using` ohne eine explizite Liste von Namen geladen werden, ist es ein Fehler, diesen Namen ohne Qualifikation zu referenzieren. Es wird daher empfohlen, dass Code, der mit zukünftigen Versionen seiner Abhängigkeiten und von Julia vorwärtskompatibel sein soll, z. B. Code in veröffentlichten Paketen, die Namen auflistet, die er aus jedem geladenen Paket verwendet, z. B. `using Foo: Foo, f` anstelle von `using Foo`.

Julia hat zwei Formen für scheinbar dasselbe, da nur `import ModuleName: f` das Hinzufügen von Methoden zu `f` *ohne einen Modulpfad* ermöglicht. Das heißt, das folgende Beispiel wird einen Fehler ausgeben:

```jldoctest module_manual
julia> using .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
ERROR: invalid method definition in Main: function NiceStuff.nice must be explicitly imported to be extended
Stacktrace:
 [1] top-level scope
   @ none:0
 [2] top-level scope
   @ none:1

```

Dieser Fehler verhindert, dass versehentlich Methoden zu Funktionen in anderen Modulen hinzugefügt werden, die Sie nur verwenden wollten.

Es gibt zwei Möglichkeiten, damit umzugehen. Sie können Funktionsnamen immer mit einem Modulpfad qualifizieren:

```jldoctest module_manual
julia> using .NiceStuff

julia> struct Cat end

julia> NiceStuff.nice(::Cat) = "nice 😸"

```

Alternativ können Sie den spezifischen Funktionsnamen `importieren`:

```jldoctest module_manual
julia> import .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
nice (generic function with 2 methods)
```

Welche Sie wählen, ist eine Frage des Stils. Die erste Form macht deutlich, dass Sie eine Methode zu einer Funktion in einem anderen Modul hinzufügen (denken Sie daran, dass die Importe und die Methodendefinition in separaten Dateien sein können), während die zweite kürzer ist, was besonders praktisch ist, wenn Sie mehrere Methoden definieren.

Sobald eine Variable über `using` oder `import` sichtbar gemacht wird, darf ein Modul keine eigene Variable mit demselben Namen erstellen. Importierte Variablen sind schreibgeschützt; das Zuweisen zu einer globalen Variable beeinflusst immer eine Variable, die dem aktuellen Modul gehört, oder es wird ein Fehler ausgelöst.

### Renaming with `as`

Ein Bezeichner, der durch `import` oder `using` in den Geltungsbereich eingeführt wird, kann mit dem Schlüsselwort `as` umbenannt werden. Dies ist nützlich, um Namenskonflikte zu umgehen und um Namen zu verkürzen. Zum Beispiel exportiert `Base` den Funktionsnamen `read`, aber das CSV.jl-Paket bietet ebenfalls `CSV.read` an. Wenn wir das CSV-Lesen viele Male aufrufen wollen, wäre es praktisch, den `CSV.`-Qualifier wegzulassen. Aber dann ist es unklar, ob wir uns auf `Base.read` oder `CSV.read` beziehen:

```julia-repl
julia> read;

julia> import CSV: read
WARNING: ignoring conflicting import of CSV.read into Main
```

Umbenennung bietet eine Lösung:

```julia-repl
julia> import CSV: read as rd
```

Importierte Pakete können auch umbenannt werden:

```julia
import BenchmarkTools as BT
```

`as` funktioniert mit `using` nur, wenn ein einzelner Bezeichner in den Geltungsbereich gebracht wird. Zum Beispiel funktioniert `using CSV: read as rd`, aber `using CSV as C` funktioniert nicht, da es auf alle exportierten Namen in `CSV` wirkt.

### Mixing multiple `using` and `import` statements

Wenn mehrere `using`- oder `import`-Anweisungen einer der oben genannten Formen verwendet werden, wird ihre Wirkung in der Reihenfolge kombiniert, in der sie erscheinen. Zum Beispiel,

```jldoctest module_manual
julia> using .NiceStuff         # exported names and the module name

julia> import .NiceStuff: nice  # allows adding methods to unqualified functions

```

würde alle exportierten Namen von `NiceStuff` und den Modulnamen selbst in den Geltungsbereich bringen und auch das Hinzufügen von Methoden zu `nice` ermöglichen, ohne es mit einem Modulnamen zu kennzeichnen.

### Handling name conflicts

Betrachten Sie die Situation, in der zwei (oder mehr) Pakete denselben Namen exportieren, wie in

```jldoctest module_manual
julia> module A
       export f
       f() = 1
       end
A
julia> module B
       export f
       f() = 2
       end
B
```

Die Anweisung `using .A, .B` funktioniert, aber wenn Sie versuchen, `f` aufzurufen, erhalten Sie einen Fehler mit einem Hinweis.

```jldoctest module_manual
julia> using .A, .B

julia> f
ERROR: UndefVarError: `f` not defined in `Main`
Hint: It looks like two or more modules export different bindings with this name, resulting in ambiguity. Try explicitly importing it from a particular module, or qualifying the name with the module it should come from.
```

Hier kann Julia nicht entscheiden, auf welches `f` Sie sich beziehen, daher müssen Sie eine Wahl treffen. Die folgenden Lösungen werden häufig verwendet:

1. Fahren Sie einfach mit qualifizierten Namen wie `A.f` und `B.f` fort. Dies macht den Kontext für den Leser Ihres Codes klar, insbesondere wenn `f` zufällig übereinstimmt, aber in verschiedenen Paketen unterschiedliche Bedeutungen hat. Zum Beispiel hat `degree` verschiedene Verwendungen in der Mathematik, den Naturwissenschaften und im Alltag, und diese Bedeutungen sollten getrennt gehalten werden.
2. Verwenden Sie das Schlüsselwort `as`, um einen oder beide Bezeichner umzubenennen, z. B.

    ```jldoctest module_manual
    julia> using .A: f as f

    julia> using .B: f as g

    ```

    würde `B.f` als `g` verfügbar machen. Hier gehen wir davon aus, dass Sie `using A` zuvor nicht verwendet haben, was `f` in den Namensraum gebracht hätte.
3. Wenn die betreffenden Namen *eine* Bedeutung teilen, ist es üblich, dass ein Modul es von einem anderen importiert oder ein leichtgewichtiges „Basis“-Paket hat, dessen einzige Funktion darin besteht, eine Schnittstelle wie diese zu definieren, die von anderen Paketen verwendet werden kann. Es ist konventionell, dass solche Paketnamen mit `...Base` enden (was nichts mit Julias `Base`-Modul zu tun hat).

### Default top-level definitions and bare modules

Module enthalten automatisch `using Core`, `using Base` und Definitionen der Funktionen [`eval`](@ref) und [`include`](@ref), die Ausdrücke/Dateien im globalen Geltungsbereich dieses Moduls auswerten.

Wenn diese Standarddefinitionen nicht gewünscht sind, können Module stattdessen mit dem Schlüsselwort [`baremodule`](@ref) definiert werden (Hinweis: `Core` wird weiterhin importiert). In Bezug auf `baremodule` sieht ein Standard-`module` so aus:

```
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```

Wenn selbst `Core` nicht gewünscht ist, kann ein Modul, das nichts importiert und keine Namen definiert, mit `Module(:YourNameHere, false, false)` definiert werden, und Code kann mit [`@eval`](@ref) oder [`Core.eval`](@ref) in es evaluiert werden:

```jldoctest
julia> arithmetic = Module(:arithmetic, false, false)
Main.arithmetic

julia> @eval arithmetic add(x, y) = $(+)(x, y)
add (generic function with 1 method)

julia> arithmetic.add(12, 13)
25
```

### Standard modules

Es gibt drei wichtige Standardmodule:

  * [`Core`](@ref) enthält alle Funktionen, die "in die" Sprache integriert sind.
  * [`Base`](@ref) enthält grundlegende Funktionen, die in fast allen Fällen nützlich sind.
  * [`Main`](@ref) ist das oberste Modul und das aktuelle Modul, wenn Julia gestartet wird.

!!! note "Standard library modules"
    Standardmäßig wird Julia mit einigen Modulen der Standardbibliothek ausgeliefert. Diese verhalten sich wie reguläre Julia-Pakete, mit dem Unterschied, dass Sie sie nicht explizit installieren müssen. Wenn Sie beispielsweise einige Unit-Tests durchführen möchten, können Sie die `Test`-Standardbibliothek wie folgt laden:

    ```julia
    using Test
    ```


## Submodules and relative paths

Module können *Untermodule* enthalten, die die gleiche Syntax `module ... end` verwenden. Sie können verwendet werden, um separate Namensräume einzuführen, was hilfreich sein kann, um komplexe Codebasen zu organisieren. Beachten Sie, dass jedes `module` seine eigene [scope](@ref scope-of-variables) einführt, sodass Untermodule nicht automatisch Namen von ihrem übergeordneten Modul „erben“.

Es wird empfohlen, dass Submodule auf andere Module innerhalb des umschließenden übergeordneten Moduls (einschließlich letzterem) mit *relativen Modulqualifikatoren* in `using`- und `import`-Anweisungen verweisen. Ein relativer Modulqualifikator beginnt mit einem Punkt (`.`), der dem aktuellen Modul entspricht, und jeder nachfolgende `.` führt zum übergeordneten Modul des aktuellen Moduls. Dies sollte, falls erforderlich, von Modulen gefolgt werden, und schließlich dem tatsächlichen Namen, auf den zugegriffen werden soll, alles durch `.` getrennt.

Betrachten Sie das folgende Beispiel, in dem das Submodul `SubA` eine Funktion definiert, die dann in seinem "Geschwister"-Modul erweitert wird:

```jldoctest module_manual
julia> module ParentModule
       module SubA
       export add_D  # exported interface
       const D = 3
       add_D(x) = x + D
       end
       using .SubA  # brings `add_D` into the namespace
       export add_D # export it from ParentModule too
       module SubB
       import ..SubA: add_D # relative path for a “sibling” module
       struct Infinity end
       add_D(x::Infinity) = x
       end
       end;

```

Sie können Code in Paketen sehen, der in einer ähnlichen Situation verwendet wird.

```jldoctest module_manual
julia> import .ParentModule.SubA: add_D

```

Allerdings funktioniert dies über [code loading](@ref code-loading), und funktioniert daher nur, wenn `ParentModule` in einem Paket ist. Es ist besser, relative Pfade zu verwenden.

Beachten Sie, dass die Reihenfolge der Definitionen auch wichtig ist, wenn Sie Werte bewerten. Berücksichtigen Sie

```julia
module TestPackage

export x, y

x = 0

module Sub
using ..TestPackage
z = y # ERROR: UndefVarError: `y` not defined in `Main`
end

y = 1

end
```

wo `Sub` versucht, `TestPackage.y` zu verwenden, bevor es definiert wurde, hat es also keinen Wert.

Aus ähnlichen Gründen können Sie keine zyklische Anordnung verwenden:

```julia
module A

module B
using ..C # ERROR: UndefVarError: `C` not defined in `Main.A`
end

module C
using ..B
end

end
```

## Module initialization and precompilation

Große Module können mehrere Sekunden zum Laden benötigen, da das Ausführen aller Anweisungen in einem Modul oft das Kompilieren einer großen Menge an Code umfasst. Julia erstellt vorcompilierte Caches des Moduls, um diese Zeit zu verkürzen.

Vorkompilierte Moduldateien (manchmal als "Cache-Dateien" bezeichnet) werden automatisch erstellt und verwendet, wenn `import` oder `using` ein Modul lädt. Wenn die Cache-Datei(en) noch nicht existieren, wird das Modul kompiliert und für die zukünftige Wiederverwendung gespeichert. Sie können auch manuell [`Base.compilecache(Base.identify_package("modulename"))`](@ref) aufrufen, um diese Dateien zu erstellen, ohne das Modul zu laden. Die resultierenden Cache-Dateien werden im Unterordner `compiled` von `DEPOT_PATH[1]` gespeichert. Wenn sich an Ihrem System nichts ändert, werden solche Cache-Dateien verwendet, wenn Sie das Modul mit `import` oder `using` laden.

Precompilation-Cache-Dateien speichern Definitionen von Modulen, Typen, Methoden und Konstanten. Sie können auch Methodenspezialisierungen und den dafür generierten Code speichern, aber dies erfordert typischerweise, dass der Entwickler explizite [`precompile`](@ref) Direktiven hinzufügt oder Arbeitslasten ausführt, die die Kompilierung während des Paketbaus erzwingen.

Wenn Sie jedoch die Abhängigkeiten des Moduls aktualisieren oder den Quellcode ändern, wird das Modul automatisch neu kompiliert, wenn Sie `using` oder `import` verwenden. Abhängigkeiten sind Module, die es importiert, der Julia-Build, Dateien, die es einfügt, oder explizite Abhängigkeiten, die von [`include_dependency(path)`](@ref) in der Moduldatei(en) deklariert werden.

Für Dateiabhängigkeiten, die durch `include` geladen werden, wird eine Änderung bestimmt, indem untersucht wird, ob die Dateigröße (`fsize`) oder der Inhalt (in einen Hash kondensiert) unverändert ist. Für Dateiabhängigkeiten, die durch `include_dependency` geladen werden, wird eine Änderung bestimmt, indem untersucht wird, ob die Änderungszeit (`mtime`) unverändert ist oder gleich der auf die nächste Sekunde gerundeten Änderungszeit (um Systeme zu berücksichtigen, die die Änderungszeit nicht mit Sub-Sekunden-Genauigkeit kopieren können). Es wird auch berücksichtigt, ob der Pfad zur Datei, der durch die Suchlogik in `require` gewählt wurde, mit dem Pfad übereinstimmt, der die Vorcompilierungsdatei erstellt hat. Außerdem wird der Satz von Abhängigkeiten berücksichtigt, die bereits in den aktuellen Prozess geladen wurden, und es werden diese Module nicht erneut kompiliert, selbst wenn sich ihre Dateien ändern oder verschwinden, um zu vermeiden, dass Inkompatibilitäten zwischen dem laufenden System und dem Vorcompilierungs-Cache entstehen. Schließlich werden Änderungen in beliebigen [compile-time preferences](@ref preferences) berücksichtigt.

Wenn Sie wissen, dass ein Modul *nicht* sicher ist, um vorab kompiliert zu werden (zum Beispiel aus einem der unten beschriebenen Gründe), sollten Sie `__precompile__(false)` in die Moduldatei einfügen (typischerweise oben platziert). Dies führt dazu, dass `Base.compilecache` einen Fehler auslöst und `using` / `import` es direkt in den aktuellen Prozess lädt und die Vorabkompilierung und das Caching überspringt. Dadurch wird auch verhindert, dass das Modul von einem anderen vorab kompilierten Modul importiert wird.

Sie sollten sich möglicherweise bestimmter Verhaltensweisen bewusst sein, die bei der Erstellung inkrementeller gemeinsam genutzter Bibliotheken auftreten, was beim Schreiben Ihres Moduls Sorgfalt erfordern kann. Zum Beispiel wird der externe Zustand nicht beibehalten. Um dies zu berücksichtigen, trennen Sie ausdrücklich alle Initialisierungsschritte, die zur *Laufzeit* erfolgen müssen, von den Schritten, die zur *Kompilierungszeit* erfolgen können. Zu diesem Zweck erlaubt es Julia, eine `__init__()`-Funktion in Ihrem Modul zu definieren, die alle Initialisierungsschritte ausführt, die zur Laufzeit erfolgen müssen. Diese Funktion wird während der Kompilierung (`--output-*`) nicht aufgerufen. Effektiv können Sie davon ausgehen, dass sie genau einmal während der Lebensdauer des Codes ausgeführt wird. Sie können sie natürlich manuell aufrufen, wenn nötig, aber der Standard ist anzunehmen, dass diese Funktion mit der Berechnung des Zustands für die lokale Maschine zu tun hat, der nicht in das kompilierte Bild aufgenommen werden muss – oder sogar nicht aufgenommen werden sollte. Sie wird aufgerufen, nachdem das Modul in einen Prozess geladen wurde, einschließlich wenn es in eine inkrementelle Kompilierung geladen wird (`--output-incremental=yes`), jedoch nicht, wenn es in einen Vollkompilierungsprozess geladen wird.

Insbesondere, wenn Sie eine `function __init__()` in einem Modul definieren, wird Julia `__init__()` sofort *nachdem* das Modul geladen wurde (z. B. durch `import`, `using` oder `require`) zur Laufzeit zum *ersten* Mal aufgerufen (d. h. `__init__` wird nur einmal aufgerufen und nur nachdem alle Anweisungen im Modul ausgeführt wurden). Da es nach dem vollständigen Import des Moduls aufgerufen wird, werden alle Untermodule oder andere importierte Module ihre `__init__`-Funktionen *vor* dem `__init__` des umschließenden Moduls aufgerufen.

Zwei typische Verwendungen von `__init__` sind das Aufrufen von Laufzeitinitialisierungsfunktionen externer C-Bibliotheken und das Initialisieren globaler Konstanten, die Zeiger enthalten, die von externen Bibliotheken zurückgegeben werden. Zum Beispiel, nehmen wir an, dass wir eine C-Bibliothek `libfoo` aufrufen, die erfordert, dass wir eine `foo_init()`-Initialisierungsfunktion zur Laufzeit aufrufen. Angenommen, wir möchten auch eine globale Konstante `foo_data_ptr` definieren, die den Rückgabewert einer `void *foo_data()`-Funktion speichert, die von `libfoo` definiert ist – diese Konstante muss zur Laufzeit (nicht zur Compile-Zeit) initialisiert werden, da sich die Zeigeradresse von Lauf zu Lauf ändern wird. Sie könnten dies erreichen, indem Sie die folgende `__init__`-Funktion in Ihrem Modul definieren:

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```

Beachten Sie, dass es durchaus möglich ist, eine globale Variable innerhalb einer Funktion wie `__init__` zu definieren; dies ist einer der Vorteile der Verwendung einer dynamischen Sprache. Indem wir sie jedoch als Konstante im globalen Gültigkeitsbereich festlegen, können wir sicherstellen, dass der Typ dem Compiler bekannt ist und ihm ermöglichen, besser optimierten Code zu generieren. Offensichtlich müssten auch alle anderen globalen Variablen in Ihrem Modul, die von `foo_data_ptr` abhängen, in `__init__` initialisiert werden.

Konstanten, die die meisten Julia-Objekte betreffen, die nicht durch [`ccall`](@ref) erzeugt werden, müssen nicht in `__init__` platziert werden: ihre Definitionen können vorcompiliert und aus dem zwischengespeicherten Modulbild geladen werden. Dies schließt komplizierte, heap-zugewiesene Objekte wie Arrays ein. Allerdings muss jede Routine, die einen rohen Zeigerwert zurückgibt, zur Laufzeit aufgerufen werden, damit die Vorcompilierung funktioniert ([`Ptr`](@ref)-Objekte werden zu Nullzeigern, es sei denn, sie sind in einem [`isbits`](@ref)-Objekt verborgen). Dies schließt die Rückgabewerte der Julia-Funktionen [`@cfunction`](@ref) und [`pointer`](@ref) ein.

Wörterbuch- und Mengentypen oder im Allgemeinen alles, was von der Ausgabe einer `hash(key)`-Methode abhängt, sind ein komplizierterer Fall. Im häufigen Fall, in dem die Schlüssel Zahlen, Zeichenfolgen, Symbole, Bereiche, `Expr` oder Kombinationen dieser Typen (über Arrays, Tupel, Mengen, Paare usw.) sind, sind sie sicher vorab zu kompilieren. Für einige andere Schlüsseltpyen, wie `Function` oder `DataType` und generische benutzerdefinierte Typen, bei denen Sie keine `hash`-Methode definiert haben, hängt die Rückfall-`hash`-Methode von der Speicheradresse des Objekts (über seine `objectid`) ab und kann sich daher von Lauf zu Lauf ändern. Wenn Sie einen dieser Schlüsseltpyen haben oder sich nicht sicher sind, können Sie zur Sicherheit dieses Wörterbuch innerhalb Ihrer `__init__`-Funktion initialisieren. Alternativ können Sie den [`IdDict`](@ref) Wörterbuchtyp verwenden, der speziell von der Vorabkompilierung behandelt wird, sodass er sicher zur Kompilierzeit initialisiert werden kann.

Beim Einsatz von Prekompilierung ist es wichtig, ein klares Verständnis für die Unterscheidung zwischen der Kompilierungsphase und der Ausführungsphase zu haben. In diesem Modus wird oft viel deutlicher, dass Julia ein Compiler ist, der die Ausführung beliebigen Julia-Codes ermöglicht, und kein eigenständiger Interpreter, der ebenfalls kompilierten Code generiert.

Andere bekannte potenzielle Fehlerszenarien sind:

1. Globale Zähler (zum Beispiel, um Objekte eindeutig zu identifizieren). Betrachten Sie den folgenden Codeausschnitt:

    ```julia
    mutable struct UniquedById
        myid::Int
        let counter = 0
            UniquedById() = new(counter += 1)
        end
    end
    ```

    Während die Absicht dieses Codes darin bestand, jeder Instanz eine eindeutige ID zu geben, wird der Zählerwert am Ende der Kompilierung aufgezeichnet. Alle nachfolgenden Verwendungen dieses inkrementell kompilierten Moduls beginnen mit demselben Zählerwert.

    Beachten Sie, dass `objectid` (das durch Hashing des Speicherzeigers funktioniert) ähnliche Probleme hat (siehe Anmerkungen zur Verwendung von `Dict` unten).

    Eine Alternative besteht darin, ein Makro zu verwenden, um [`@__MODULE__`](@ref) zu erfassen und es zusammen mit dem aktuellen `counter`-Wert zu speichern. Es könnte jedoch besser sein, den Code so umzugestalten, dass er nicht von diesem globalen Zustand abhängt.
2. Assoziative Sammlungen (wie `Dict` und `Set`) müssen in `__init__` neu gehasht werden. (In Zukunft könnte ein Mechanismus bereitgestellt werden, um eine Initialisierungsfunktion zu registrieren.)
3. Abhängig von den zur Kompilierungszeit bestehenden Nebeneffekten, die zur Ladezeit bestehen bleiben. Beispiele sind: Modifizieren von Arrays oder anderen Variablen in anderen Julia-Modulen; Beibehalten von Handles zu offenen Dateien oder Geräten; Speichern von Zeigern auf andere Systemressourcen (einschließlich Speicher);
4. Erstellen von versehentlichen "Kopien" des globalen Zustands aus einem anderen Modul, indem man direkt darauf verweist, anstatt über seinen Suchpfad. Zum Beispiel (im globalen Gültigkeitsbereich):

    ```julia
    #mystdout = Base.stdout #= will not work correctly, since this will copy Base.stdout into this module =#
    # instead use accessor functions:
    getstdout() = Base.stdout #= best option =#
    # or move the assignment into the runtime:
    __init__() = global mystdout = Base.stdout #= also works =#
    ```

Es werden mehrere zusätzliche Einschränkungen für die Operationen festgelegt, die beim Vorabkompilieren von Code durchgeführt werden können, um dem Benutzer zu helfen, andere Fehlverhalten zu vermeiden:

1. Aufruf von [`eval`](@ref), um einen Nebeneffekt in einem anderen Modul zu verursachen. Dies wird auch eine Warnung auslösen, wenn das Flag für die inkrementelle Vorabkompilierung gesetzt ist.
2. `global const`-Anweisungen aus dem lokalen Geltungsbereich, nachdem `__init__()` gestartet wurde (siehe Issue #12010 für Pläne, einen Fehler dafür hinzuzufügen)
3. Das Ersetzen eines Moduls ist ein Laufzeitfehler beim Durchführen einer inkrementellen Vorabkompilierung.

Einige weitere Punkte, die zu beachten sind:

1. Es wird kein Code-Neuladen / keine Cache-Invalidierung durchgeführt, nachdem Änderungen an den Quell-Dateien selbst vorgenommen wurden (einschließlich durch `Pkg.update`), und es wird keine Bereinigung nach `Pkg.rm` durchgeführt.
2. Das Speicherfreigabeverhalten eines umgeformten Arrays wird bei der Vorabkompilierung ignoriert (jede Ansicht erhält ihre eigene Kopie).
3. Erwartung, dass das Dateisystem zwischen der Kompilierungszeit und der Laufzeit unverändert bleibt, z. B. [`@__FILE__`](@ref)/`source_path()` um Ressourcen zur Laufzeit zu finden, oder das BinDeps `@checked_lib` Makro. Manchmal ist dies unvermeidlich. Wenn möglich, kann es jedoch eine gute Praxis sein, Ressourcen zur Kompilierungszeit in das Modul zu kopieren, damit sie zur Laufzeit nicht gefunden werden müssen.
4. `WeakRef`-Objekte und Finalisierer werden derzeit vom Serializer nicht ordnungsgemäß behandelt (dies wird in einer kommenden Version behoben).
5. Es ist in der Regel am besten, Referenzen auf Instanzen interner Metadatenobjekte wie `Method`, `MethodInstance`, `MethodTable`, `TypeMapLevel`, `TypeMapEntry` und Felder dieser Objekte zu vermeiden, da dies den Serializer verwirren kann und möglicherweise nicht zu dem gewünschten Ergebnis führt. Es ist nicht unbedingt ein Fehler, dies zu tun, aber Sie müssen sich einfach darauf vorbereiten, dass das System versuchen wird, einige davon zu kopieren und andere als eine einzige eindeutige Instanz zu erstellen.

Es ist manchmal hilfreich, während der Modulentwicklung die inkrementelle Vorcompilierung auszuschalten. Der Befehlszeilenparameter `--compiled-modules={yes|no|existing}` ermöglicht es Ihnen, die Modulvorcompilierung ein- und auszuschalten. Wenn Julia mit `--compiled-modules=no` gestartet wird, werden die serialisierten Module im Kompiliercache beim Laden von Modulen und Modulabhängigkeiten ignoriert. In einigen Fällen möchten Sie möglicherweise vorhandene vorcompilierte Module laden, aber keine neuen erstellen. Dies kann erreicht werden, indem Sie Julia mit `--compiled-modules=existing` starten. Eine feinere Steuerung ist mit `--pkgimages={yes|no|existing}` verfügbar, die nur die Speicherung von nativen Codes während der Vorcompilierung betrifft. `Base.compilecache` kann weiterhin manuell aufgerufen werden. Der Zustand dieses Befehlszeilenparameters wird an `Pkg.build` übergeben, um die automatische Auslösung der Vorcompilierung beim Installieren, Aktualisieren und expliziten Erstellen von Paketen zu deaktivieren.

Sie können auch einige Prekompilierungsfehler mit Umgebungsvariablen debuggen. Das Setzen von `JULIA_VERBOSE_LINKING=true` kann helfen, Fehler beim Verlinken von gemeinsam genutzten Bibliotheken von kompiliertem nativen Code zu beheben. Siehe den **Entwicklerdokumentations**-Teil des Julia-Handbuchs, wo Sie weitere Details im Abschnitt finden, der Julias Interna unter "Paketbilder" dokumentiert.
