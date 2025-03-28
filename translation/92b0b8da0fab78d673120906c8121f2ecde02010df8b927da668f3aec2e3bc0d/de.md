# Julia SSA-form IR

Julia verwendet eine statische Einzuzuweisung zwischenliegende Darstellung ([SSA IR](https://en.wikipedia.org/wiki/Static_single-assignment_form)), um Optimierungen durchzuführen. Diese IR unterscheidet sich von LLVM IR und ist einzigartig für Julia. Sie ermöglicht spezifische Optimierungen für Julia.

1. Basisblöcke (Bereiche ohne Kontrollfluss) sind ausdrücklich annotiert.
2. if/else und Schleifen werden in `goto`-Anweisungen umgewandelt.
3. Zeilen mit mehreren Operationen werden durch die Einführung von Variablen in mehrere Zeilen aufgeteilt.

Zum Beispiel der folgende Julia-Code:

```julia
function foo(x)
    y = sin(x)
    if x > 5.0
        y = y + cos(x)
    end
    return exp(2) + y
end
```

wenn mit einem `Float64`-Argument aufgerufen wird, wird es übersetzt in:

```julia
using InteractiveUtils
@code_typed foo(1.0)
```

```llvm
CodeInfo(
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
2 ─ %4 = invoke Main.cos(x::Float64)::Float64
└── %5 = Base.add_float(%1, %4)::Float64
3 ┄ %6 = φ (#2 => %5, #1 => %1)::Float64
│   %7 = Base.add_float(7.38905609893065, %6)::Float64
└──      return %7
) => Float64
```

In diesem Beispiel können wir all diese Änderungen sehen.

1. Der erste grundlegende Block ist alles in

```llvm
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
```

2. Die `if`-Anweisung wird in `goto #3 if not %2` übersetzt, was zum 3. Basisblock führt, wenn `x>5` nicht erfüllt ist, und andernfalls zum zweiten Basisblock führt.
3. `%2` ist ein SSA-Wert, der eingeführt wurde, um `x > 5` darzustellen.

## Background

Beginnend mit Julia 0.7 verwenden Teile des Compilers eine neue [SSA-form](https://en.wikipedia.org/wiki/Static_single_assignment_form) Zwischenrepräsentation (IR). Historisch gesehen generierte der Compiler direkt LLVM IR aus einer reduzierten Form des Julia AST. Diese Form hatte die meisten syntaktischen Abstraktionen entfernt, sah aber immer noch sehr ähnlich wie ein abstrakter Syntaxbaum aus. Im Laufe der Zeit wurden zur Erleichterung von Optimierungen SSA-Werte in dieses IR eingeführt und das IR wurde linearisiert (d.h. in eine Form umgewandelt, in der Funktionsargumente nur SSA-Werte oder Konstanten sein konnten). Nicht-SSA-Werte (Slots) blieben jedoch im IR aufgrund des Fehlens von Phi-Knoten im IR (notwendig für Rückkanten und das erneute Zusammenführen von bedingtem Kontrollfluss). Dies minderte den Nutzen der SSA-Formdarstellung bei der Durchführung von Optimierungen im mittleren Ende erheblich. Einige heldenhafte Anstrengungen wurden unternommen, um diese Optimierungen ohne eine vollständige SSA-Formdarstellung zum Laufen zu bringen, aber das Fehlen einer solchen Darstellung erwies sich letztendlich als hinderlich.

## Categories of IR nodes

Die SSA-IR-Darstellung hat vier Kategorien von IR-Knoten: Phi, Pi, PhiC und Upsilon-Knoten (die letzten beiden werden nur für die Ausnahmebehandlung verwendet).

### Phi nodes and Pi nodes

Phi-Knoten sind Teil der generischen SSA-Abstraktion (siehe den obigen Link, wenn Sie mit dem Konzept nicht vertraut sind). Im Julia-IR werden diese Knoten dargestellt als:

```
struct PhiNode
    edges::Vector{Int32}
    values::Vector{Any}
end
```

wo wir sicherstellen, dass beide Vektoren immer die gleiche Länge haben. In der kanonischen Darstellung (derjenigen, die von Codegen und dem Interpreter verarbeitet wird) geben die Kantenwerte die Nummern der "come-from"-Anweisungen an (d.h. wenn eine Kante einen Eintrag von `15` hat, muss es ein `goto`, `gotoifnot` oder einen impliziten Fall durch von Anweisung `15` geben, der auf diesen Phi-Knoten abzielt). Werte sind entweder SSA-Werte oder Konstanten. Es ist auch möglich, dass ein Wert nicht zugewiesen ist, wenn die Variable auf diesem Pfad nicht definiert wurde. Allerdings werden Überprüfungen auf undefinierte Werte explizit eingefügt und nach den Optimierungen im mittleren Ende als Booleans dargestellt, sodass Codegeneratoren davon ausgehen können, dass jede Verwendung eines Phi-Knotens einen zugewiesenen Wert im entsprechenden Slot hat. Es ist auch legal, dass die Zuordnung unvollständig ist, d.h. dass ein Phi-Knoten fehlende eingehende Kanten hat. In diesem Fall muss dynamisch garantiert werden, dass der entsprechende Wert nicht verwendet wird.

Beachten Sie, dass SSA semantisch nach dem Terminator des entsprechenden Vorgängers ("am Rand") auftritt. Folglich, wenn mehrere Phi-Knoten am Anfang eines Basisblocks erscheinen, werden sie gleichzeitig ausgeführt. Das bedeutet, dass in dem folgenden IR-Ausschnitt, wenn wir aus Block `23` kamen, `%46` den Wert übernimmt, der mit `%45` *bevor* wir diesen Block betreten haben.

```julia
%45 = φ (#18 => %23, #23 => %50)
%46 = φ (#18 => 1.0, #23 => %45)
```

PiNodes kodieren statisch bewiesene Informationen, die in grundlegenden Blöcken, die von einem bestimmten Pi-Knoten dominiert werden, implizit angenommen werden können. Sie sind konzeptionell äquivalent zu der Technik, die in dem Papier [ABCD: Eliminating Array Bounds Checks on Demand](https://dl.acm.org/citation.cfm?id=358438.349342) eingeführt wurde, oder den Prädikat-Info-Knoten in LLVM. Um zu sehen, wie sie funktionieren, betrachten Sie z.B.

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    # use x
else
    # use x
end
```

Wir können eine Prädikateinfügung durchführen und dies in Folgendes umwandeln:

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    %x_int = PiNode(x, Int)
    # use %x_int
else
    %x_float = PiNode(x, Float64)
    # use %x_float
end
```

Pi-Knoten werden im Interpreter allgemein ignoriert, da sie keinen Einfluss auf die Werte haben, können jedoch manchmal zu einer Codegenerierung im Compiler führen (z. B. um von einer impliziten Unionsteilung zu einer einfachen unboxed Darstellung zu wechseln). Der Hauptnutzen von Pi-Knoten ergibt sich aus der Tatsache, dass die Pfadbedingungen der Werte einfach durch das Durchlaufen der Def-Use-Kette akkumuliert werden können, was im Allgemeinen für die meisten Optimierungen, die sich ohnehin um diese Bedingungen kümmern, durchgeführt wird.

### PhiC nodes and Upsilon nodes

Die Ausnahmebehandlung kompliziert die SSA-Geschichte mäßig, da die Ausnahmebehandlung zusätzliche Kontrollflusskanten in die IR einführt, über die Werte verfolgt werden müssen. Ein Ansatz, um dies zu tun, der von LLVM verfolgt wird, besteht darin, Aufrufe, die Ausnahmen auslösen können, in die Terminatoren von Basisblöcken zu integrieren und eine explizite Kontrollflusskante zum Catch-Handler hinzuzufügen:

```
invoke @function_that_may_throw() to label %regular unwind to %catch

regular:
# Control flow continues here

catch:
# Exceptions go here
```

Allerdings ist dies problematisch in einer Sprache wie Julia, in der wir zu Beginn der Optimierungspipeline nicht wissen, welche Aufrufe Fehler auslösen. Wir müssten konservativ annehmen, dass jeder Aufruf (der in Julia jede Anweisung ist) einen Fehler auslöst. Dies hätte mehrere negative Auswirkungen. Einerseits würde es im Wesentlichen den Geltungsbereich jedes grundlegenden Blocks auf einen einzigen Aufruf reduzieren, was den Zweck, Operationen auf der Ebene des grundlegenden Blocks durchzuführen, zunichte machen würde. Andererseits hätte jeder Catch-Grundblock `n*m` phi-Knoten-Argumente (`n`, die Anzahl der Anweisungen im kritischen Bereich, `m` die Anzahl der lebenden Werte durch den Catch-Block).

Um dies zu umgehen, verwenden wir eine Kombination aus `Upsilon`- und `PhiC`-Knoten (das C steht für `catch`, geschrieben `φᶜ` im IR-Pretty-Printer, da der Unicode-Tiefgestellt c nicht verfügbar ist). Es gibt mehrere Möglichkeiten, über diese Knoten nachzudenken, aber vielleicht ist es am einfachsten, jeden `PhiC` als einen Ladevorgang aus einem einzigartigen Store-many, Read-once-Slot zu betrachten, wobei `Upsilon` die entsprechende Speicheroperation ist. Der `PhiC` hat eine Operandenliste aller Upsilon-Knoten, die in seinen impliziten Slot speichern. Die `Upsilon`-Knoten hingegen zeichnen nicht auf, in welchen `PhiC`-Knoten sie speichern. Dies geschieht für eine natürlichere Integration mit dem Rest des SSA-IR. Zum Beispiel, wenn es keine weiteren Verwendungen eines `PhiC`-Knotens gibt, ist es sicher, ihn zu löschen, und dasselbe gilt für einen `Upsilon`-Knoten. In den meisten IR-Pässen können `PhiC`-Knoten wie `Phi`-Knoten behandelt werden. Man kann den Verwendungs-def-Ketten durch sie folgen, und sie können zu neuen `PhiC`-Knoten und neuen `Upsilon`-Knoten (an denselben Stellen wie die ursprünglichen `Upsilon`-Knoten) angehoben werden. Das Ergebnis dieses Schemas ist, dass die Anzahl der `Upsilon`-Knoten (und `PhiC`-Argumente) proportional zur Anzahl der zugewiesenen Werte an eine bestimmte Variable (vor der SSA-Konvertierung) ist, anstatt zur Anzahl der Anweisungen im kritischen Bereich.

Um dieses Schema in Aktion zu sehen, betrachten Sie die Funktion

```julia
@noinline opaque() = invokelatest(identity, nothing) # Something opaque
function foo()
    local y
    x = 1
    try
        y = 2
        opaque()
        y = 3
        error()
    catch
    end
    (x, y)
end
```

Der entsprechende IR (mit entfernten irrelevanten Typen) ist:

```
1 ─       nothing::Nothing
2 ─ %2  = $(Expr(:enter, #4))
3 ─ %3  = ϒ (false)
│   %4  = ϒ (#undef)
│   %5  = ϒ (1)
│   %6  = ϒ (true)
│   %7  = ϒ (2)
│         invoke Main.opaque()::Any
│   %9  = ϒ (true)
│   %10 = ϒ (3)
│         invoke Main.error()::Union{}
└──       $(Expr(:unreachable))::Union{}
4 ┄ %13 = φᶜ (%3, %6, %9)::Bool
│   %14 = φᶜ (%4, %7, %10)::Core.Compiler.MaybeUndef(Int64)
│   %15 = φᶜ (%5)::Core.Const(1)
└──       $(Expr(:leave, Core.SSAValue(2)))
5 ─       $(Expr(:pop_exception, :(%2)))::Any
│         $(Expr(:throw_undef_if_not, :y, :(%13)))::Any
│   %19 = Core.tuple(%15, %14)
└──       return %19
```

Beachten Sie insbesondere, dass jeder Wert, der in den kritischen Bereich gelangt, einen Upsilon-Knoten oben im kritischen Bereich erhält. Dies liegt daran, dass Catch-Blöcke als unsichtbare Kontrollflusskante von außerhalb der Funktion betrachtet werden. Infolgedessen dominiert kein SSA-Wert die Catch-Blöcke, und alle eingehenden Werte müssen durch einen `φᶜ`-Knoten kommen.

## Main SSA data structure

Die Hauptdatenstruktur `SSAIR` ist eine Diskussion wert. Sie ist inspiriert von LLVM und Webkits B3 IR. Der Kern der Datenstruktur ist ein flaches Vektor von Anweisungen. Jede Anweisung wird implizit basierend auf ihrer Position im Vektor einem SSA-Wert zugewiesen (d.h. das Ergebnis der Anweisung an Index 1 kann mit `SSAValue(1)` usw. abgerufen werden). Für jeden SSA-Wert halten wir zusätzlich seinen Typ fest. Da SSA-Werte definitionsgemäß nur einmal zugewiesen werden, ist dieser Typ auch der Ergebnistyp des Ausdrucks am entsprechenden Index. Diese Darstellung ist jedoch recht effizient (da die Zuweisungen nicht explizit codiert werden müssen), hat sie natürlich den Nachteil, dass die Reihenfolge semantisch signifikant ist, sodass Umstellungen und Einfügungen die Anweisungsnummern ändern. Darüber hinaus führen wir keine Verwendungsliste (d.h. es ist unmöglich, von einer Definition zu all ihren Verwendungen zu gelangen, ohne diese Zuordnung explizit zu berechnen – Def-Listen sind jedoch trivial, da man die entsprechende Anweisung anhand des Index nachschlagen kann), sodass die LLVM-Stil RAUW (replace-all-uses-with) Operation nicht verfügbar ist.

Stattdessen tun wir Folgendes:

  * Wir halten einen separaten Puffer von Knoten zum Einfügen (einschließlich der Position, an der sie eingefügt werden sollen, des Typs des entsprechenden Wertes und des Knotens selbst). Diese Knoten sind nach ihrem Auftreten im Einfügepuffer nummeriert, sodass ihre Werte sofort anderswo im IR verwendet werden können (d.h. wenn es 12 Anweisungen in der ursprünglichen Anweisungsliste gibt, wird die erste neue Anweisung als `SSAValue(13)` zugänglich sein).
  * RAUW-Stil-Operationen werden durchgeführt, indem der entsprechende Anweisungsindex auf den Ersetzungswert gesetzt wird.
  * Aussagen werden gelöscht, indem die entsprechende Aussage auf `nichts` gesetzt wird (dies ist im Wesentlichen nur eine spezielle Konvention des Obigen).
  * Wenn es irgendwelche Verwendungen der Aussage gibt, die gelöscht wird, werden sie auf `nichts` gesetzt.

Es gibt eine `compact!`-Funktion, die die oben genannte Datenstruktur komprimiert, indem sie die Einfügung von Knoten an der entsprechenden Stelle, triviale Kopierweiterleitung und Umbenennung von Verwendungen in geänderte SSA-Werte durchführt. Der clevere Teil dieses Schemas ist jedoch, dass diese Komprimierung faul als Teil des nachfolgenden Durchgangs durchgeführt werden kann. Die meisten Optimierungsdurchgänge müssen die gesamte Liste der Anweisungen durchlaufen und dabei Analysen oder Modifikationen vornehmen. Wir bieten einen `IncrementalCompact`-Iterator an, der verwendet werden kann, um über die Anweisungsliste zu iterieren. Er führt alle notwendigen Komprimierungen durch und gibt den neuen Index des Knotens sowie den Knoten selbst zurück. Es ist an diesem Punkt legal, Def-Use-Ketten zu durchlaufen sowie Modifikationen oder Löschungen am IR vorzunehmen (Einfügungen sind jedoch nicht erlaubt).

Die Idee hinter dieser Anordnung ist, dass, da die Optimierungspässe ohnehin auf den entsprechenden Speicher zugreifen müssen und die entsprechenden Speicherzugriffsstrafe verursachen, das Durchführen der zusätzlichen Verwaltungsaufgaben vergleichsweise wenig Overhead haben sollte (und den Overhead des Aufrechterhaltens dieser Datenstrukturen während der IR-Modifikation einsparen sollte).
