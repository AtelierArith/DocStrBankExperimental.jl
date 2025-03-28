# `EscapeAnalysis`

`Core.Compiler.EscapeAnalysis` ist ein Compiler-Dienstprogramm-Modul, das darauf abzielt, die Escape-Informationen von [Julia's SSA-form IR](@ref Julia-SSA-form-IR), auch bekannt als `IRCode`, zu analysieren.

Diese Escape-Analyse zielt darauf ab:

  * Nutzen Sie Julias hochgradige Semantik, insbesondere um über Ausstiege und Aliasierung durch interprozedurale Aufrufe nachzudenken.
  * seien Sie vielseitig genug, um für verschiedene Optimierungen verwendet zu werden, einschließlich [alias-aware SROA](https://github.com/JuliaLang/julia/pull/43888), [early `finalize` insertion](https://github.com/JuliaLang/julia/pull/44056), [copy-free `ImmutableArray` construction](https://github.com/JuliaLang/julia/pull/42465), Stapelzuweisung von veränderlichen Objekten und so weiter.
  * erreichen Sie eine einfache Implementierung, die auf einer vollständig rückwärtsgerichteten Datenflussanalyse-Implementierung basiert, sowie ein neues Gitterdesign, das orthogonale Gittereigenschaften kombiniert.

## Try it out!

Sie können die Escape-Analyse ausprobieren, indem Sie das `EAUtils.jl`-Hilfsskript laden, das die praktischen Einträge `code_escapes` und `@code_escapes` zu Test- und Debuggingzwecken definiert:

```@repl EAUtils
let JULIA_DIR = normpath(Sys.BINDIR, "..", "share", "julia")
    # load `EscapeAnalysis` module to define the core analysis code
    include(normpath(JULIA_DIR, "base", "compiler", "ssair", "EscapeAnalysis", "EscapeAnalysis.jl"))
    using .EscapeAnalysis
    # load `EAUtils` module to define the utilities
    include(normpath(JULIA_DIR, "test", "compiler", "EscapeAnalysis", "EAUtils.jl"))
    using .EAUtils
end

mutable struct SafeRef{T}
    x::T
end
Base.getindex(x::SafeRef) = x.x;
Base.setindex!(x::SafeRef, v) = x.x = v;
Base.isassigned(x::SafeRef) = true;
get′(x) = isassigned(x) ? x[] : throw(x);

result = code_escapes((String,String,String,String)) do s1, s2, s3, s4
    r1 = Ref(s1)
    r2 = Ref(s2)
    r3 = SafeRef(s3)
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    s3 = get′(r3)       # still `r3` doesn't escape fully
    s4 = sizeof(s4)     # the argument `s4` doesn't escape here
    return s2, s3, s4
end
```

Die Symbole an der Seite jedes Aufrufarguments und der SSA-Anweisungen bedeuten Folgendes:

  * `◌` (plain): Dieser Wert wird nicht analysiert, da die Escape-Informationen davon ohnehin nicht verwendet werden (wenn das Objekt beispielsweise `isbitstype` ist).
  * `✓` (grün oder cyan): dieser Wert entkommt niemals (`has_no_escape(result.state[x])` gilt), blau gefärbt, wenn auch `has_arg_escape(result.state[x])` gilt
  * `↑` (blau oder gelb): dieser Wert kann über die Rückgabe an den Aufrufer entkommen (`has_return_escape(result.state[x])` gilt), gelb gefärbt, wenn er auch unhandled thrown escape hat (`has_thrown_escape(result.state[x])` gilt)
  * `X` (rot): dieser Wert kann an einen Ort entkommen, den die Escape-Analyse nicht nachvollziehen kann, wie das Entkommen in einen globalen Speicher (`has_all_escape(result.state[x])` gilt)
  * `*` (fett): der Fluchtzustand dieses Wertes liegt zwischen dem `ReturnEscape` und `AllEscape` in der partiellen Ordnung von [`EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo), gelb gefärbt, wenn es unbehandelte geworfene Flucht gibt (`has_thrown_escape(result.state[x])` gilt)
  * `′`: dieser Wert hat zusätzliche Objektfeld-/Array-Elementinformationen in seiner `AliasInfo`-Eigenschaft

Die Escape-Information jedes Aufrufarguments und SSA-Werts kann programmgesteuert inspiziert werden, wie folgt:

```@repl EAUtils
result.state[Core.Argument(3)] # get EscapeInfo of `s2`

result.state[Core.SSAValue(3)] # get EscapeInfo of `r3`
```

## Analysis Design

### Lattice Design

`EscapeAnalysis` wird als ein [data-flow analysis](https://en.wikipedia.org/wiki/Data-flow_analysis) implementiert, das auf einem Gitter von [`x::EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo) arbeitet, das aus den folgenden Eigenschaften besteht:

  * `x.Analyzed::Bool`: nicht formell Teil des Lattices, zeigt nur an, ob `x` analysiert wurde oder nicht
  * `x.ReturnEscape::BitSet`: zeichnet SSA-Anweisungen auf, bei denen `x` über die Rückgabe an den Aufrufer entkommen kann
  * `x.ThrownEscape::BitSet`: zeichnet SSA-Anweisungen auf, bei denen `x` als Ausnahme geworfen werden kann (verwendet für die [exception handling](@ref EA-Exception-Handling), die unten beschrieben ist)
  * `x.AliasInfo`: enthält alle möglichen Werte, die auf Felder oder Array-Elemente von `x` aliasiert werden können (verwendet für die [alias analysis](@ref EA-Alias-Analysis), die unten beschrieben ist)
  * `x.ArgEscape::Int` (noch nicht implementiert): zeigt an, dass es über `setfield!` an den Aufrufer durch Argument(e) entkommen wird.

Diese Attribute können kombiniert werden, um ein partielles Gitter zu erstellen, das eine endliche Höhe hat, vorausgesetzt, dass ein Eingabeprogramm eine endliche Anzahl von Anweisungen hat, was durch Julias Semantik gewährleistet ist. Der clevere Teil dieses Gitterdesigns besteht darin, dass es eine einfachere Implementierung von Gitteroperationen ermöglicht, indem es ihnen erlaubt, jede Gittereigenschaft separat zu behandeln[^LatticeDesign].

### Backward Escape Propagation

Diese Implementierung der Escape-Analyse basiert auf dem Datenflussalgorithmus, der im Papier[^MM02] beschrieben ist. Die Analyse arbeitet auf dem Gitter von `EscapeInfo` und überführt Gitterelemente von unten nach oben, bis jedes Gitterelement zu einem festen Punkt konvergiert, indem ein (konzeptioneller) Arbeitsbereich aufrechterhalten wird, der Programmzähler enthält, die den verbleibenden SSA-Anweisungen entsprechen, die analysiert werden sollen. Die Analyse verwaltet einen einzigen globalen Zustand, der `EscapeInfo` jedes Arguments und jeder SSA-Anweisung verfolgt, aber beachten Sie auch, dass einige Fluss-Sensitivität als Programmzähler kodiert ist, die in der `ReturnEscape`-Eigenschaft von `EscapeInfo` aufgezeichnet sind, die später mit der Dominanzanalyse kombiniert werden kann, um bei Bedarf über Fluss-Sensitivität zu argumentieren.

Ein markantes Design dieser Fluchtanalyse ist, dass sie vollständig *rückwärts* ist, d.h. Fluchtinformationen fließen *von Verwendungen zu Definitionen*. Zum Beispiel analysiert die Fluchtanalyse im folgenden Code-Snippet zuerst die Anweisung `return %1` und legt `ReturnEscape` auf `%1` (entsprechend `obj`) fest, und dann analysiert sie `%1 = %new(Base.RefValue{String, _2}))` und propagiert das auf `%1` auferlegte `ReturnEscape` auf das Aufrufargument `_2` (entsprechend `s`):

```@repl EAUtils
code_escapes((String,)) do s
    obj = Ref(s)
    return obj
end
```

Die wichtigste Beobachtung hier ist, dass diese rückwärtsgerichtete Analyse es ermöglicht, dass Fluchtinformationen natürlich entlang der Verwendung-Definition-Kette fließen, anstatt entlang des Kontrollflusses[^BackandForth]. Infolgedessen ermöglicht dieses Schema eine einfache Implementierung der Fluchtanalyse, z. B. kann `PhiNode` einfach behandelt werden, indem Fluchtinformationen, die auf einen `PhiNode` auferlegt werden, an seine Vorgängerwerte propagiert werden:

```@repl EAUtils
code_escapes((Bool, String, String)) do cnd, s, t
    if cnd
        obj = Ref(s)
    else
        obj = Ref(t)
    end
    return obj
end
```

### [Alias Analysis](@id EA-Alias-Analysis)

`EscapeAnalysis` implementiert eine rückwärtsgerichtete Feldanalyse, um über die auf Objektfelder ausgeübten Entweichungen mit gewisser Genauigkeit zu argumentieren, und die `x::EscapeInfo`-Eigenschaft `x.AliasInfo` existiert zu diesem Zweck. Sie zeichnet alle möglichen Werte auf, die an "Nutzungs"-Stellen auf Felder von `x` aliasiert werden können, und dann wird die Entweichungsinformation dieser aufgezeichneten Werte später an den tatsächlichen Feldwerten an "Definitions"-Stellen propagiert. Genauer gesagt, zeichnet die Analyse einen Wert auf, der an ein Feld eines Objekts aliasiert sein kann, indem sie den `getfield`-Aufruf analysiert, und propagiert dann seine Entweichungsinformation an das Feld, wenn sie den `%new(...)`-Ausdruck oder den `setfield!`-Aufruf analysiert[^Dynamism].

```@repl EAUtils
code_escapes((String,)) do s
    obj = SafeRef("init")
    obj[] = s
    v = obj[]
    return v
end
```

Im dem obigen Beispiel wird `ReturnEscape`, das auf `%3` (entsprechend `v`) angewendet wird, *nicht* direkt an `%1` (entsprechend `obj`) weitergegeben, sondern `ReturnEscape` wird nur an `_2` (entsprechend `s`) weitergegeben. Hier wird `%3` in der `AliasInfo`-Eigenschaft von `%1` aufgezeichnet, da es auf das erste Feld von `%1` aliasiert werden kann, und wenn dann `Base.setfield!(%1, :x, _2)::String` analysiert wird, wird diese Escape-Information an `_2` weitergegeben, aber nicht an `%1`.

So `EscapeAnalysis` verfolgt, welche IR-Elemente über eine `getfield`-`%new`/`setfield!`-Kette aliasiert werden können, um die Entweichungen von Objektfeldern zu analysieren. Tatsächlich muss diese Alias-Analyse jedoch verallgemeinert werden, um auch andere IR-Elemente zu behandeln. Dies liegt daran, dass im Julia IR dasselbe Objekt manchmal durch verschiedene IR-Elemente dargestellt wird, und wir sollten sicherstellen, dass diese verschiedenen IR-Elemente, die tatsächlich dasselbe Objekt darstellen können, die gleichen Entweichungsinformationen teilen. IR-Elemente, die dasselbe Objekt wie ihre Operanden zurückgeben, wie `PiNode` und `typeassert`, können diese IR-Ebene-Aliasierung verursachen und erfordern daher, dass die Entweichungsinformationen, die auf einen solchen aliasierten Wert angewendet werden, zwischen ihnen geteilt werden. Interessanterweise ist es auch notwendig, um korrekt über Mutationen auf `PhiNode` nachzudenken. Lassen Sie uns das folgende Beispiel betrachten:

```@repl EAUtils
code_escapes((Bool, String,)) do cond, x
    if cond
        ϕ2 = ϕ1 = SafeRef("foo")
    else
        ϕ2 = ϕ1 = SafeRef("bar")
    end
    ϕ2[] = x
    y = ϕ1[]
    return y
end
```

`ϕ1 = %5` und `ϕ2 = %6` sind aliasiert und daher muss `ReturnEscape`, das auf `%8 = Base.getfield(%6, :x)::String` (entsprechend `y = ϕ1[]`) auferlegt wird, auf `Base.setfield!(%5, :x, _3)::String` (entsprechend `ϕ2[] = x`) propagiert werden. Damit solche Fluchtinformationen korrekt propagiert werden, sollte die Analyse erkennen, dass auch die *Vorgänger* von `ϕ1` und `ϕ2` aliasiert sein können und ihre Fluchtinformationen gleichsetzen.

Eine interessante Eigenschaft solcher Alias-Informationen ist, dass sie am "Nutzungs"-Standort nicht bekannt sind, sondern nur am "Definitions"-Standort abgeleitet werden können (da Aliasing konzeptionell dem Zuweisen entspricht), und daher passt es nicht natürlich in eine rückwärtsgerichtete Analyse. Um Fluchtinformationen effizient zwischen verwandten Werten zu propagieren, verwendet EscapeAnalysis.jl einen Ansatz, der von dem Fluchtanalyse-Algorithmus inspiriert ist, der in einem alten JVM-Papier[^JVM05] erklärt wird. Das heißt, zusätzlich zur Verwaltung von Fluchtgitterelementen verwaltet die Analyse auch eine "equi"-Alias-Menge, eine disjunkte Menge von aliasierten Argumenten und SSA-Anweisungen. Die Alias-Menge verwaltet Werte, die einander aliasiert werden können, und ermöglicht es, Fluchtinformationen, die auf einen dieser aliasierten Werte auferlegt werden, zwischen ihnen zu egalisieren.

### [Array Analysis](@id EA-Array-Analysis)

Die oben beschriebene Alias-Analyse für Objektfelder kann auch verallgemeinert werden, um Array-Operationen zu analysieren. `EscapeAnalysis` implementiert Handhabungen für verschiedene primitive Array-Operationen, sodass es Escapes über die `arrayref`-`arrayset`-Nutzungs-Definitionskette propagieren kann und nicht zu konservativ mit allokierten Arrays umgeht:

```@repl EAUtils
code_escapes((String,)) do s
    ary = Any[]
    push!(ary, SafeRef(s))
    return ary[1], length(ary)
end
```

Im dem obigen Beispiel versteht `EscapeAnalysis`, dass `%20` und `%2` (entsprechend dem zugewiesenen Objekt `SafeRef(s)`) über die `arrayset`-`arrayref`-Kette aliasiert sind und `ReturnEscape` auf sie auferlegt, aber nicht auf das zugewiesene Array `%1` (entsprechend `ary`). `EscapeAnalysis` auferlegt weiterhin `ThrownEscape` auf `ary`, da es auch potenzielle Fluchten über `BoundsError` berücksichtigen muss, aber beachten Sie auch, dass solche unbehandelten `ThrownEscape` oft ignoriert werden können, wenn die Zuweisung von `ary` optimiert wird.

Darüber hinaus kann `EscapeAnalysis` in Fällen, in denen die Array-Indexinformationen sowie die Array-Dimensionen *genau* bekannt sind, sogar über "pro-Element" Aliasing über die `arrayref`-`arrayset`-Kette nachdenken, da `EscapeAnalysis` eine "pro-Feld" Alias-Analyse für Objekte durchführt:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Vector{Any}(undef, 2)
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

Beachten Sie, dass `ReturnEscape` nur auf `%2` (entsprechend `SafeRef(s)`) und nicht auf `%4` (entsprechend `SafeRef(t)`) angewendet wird. Dies liegt daran, dass die Dimension des zugewiesenen Arrays und die Indizes, die an allen `arrayref`/`arrayset`-Operationen beteiligt sind, als konstante Informationen verfügbar sind und `EscapeAnalysis` verstehen kann, dass `%6` auf `%2` verweist, aber niemals auf `%4`. In einem solchen Fall werden die nachfolgenden Optimierungspässe in der Lage sein, `Base.arrayref(true, %1, 1)::Any` durch `%2` (auch bekannt als "Load-Forwarding") zu ersetzen und schließlich die Zuweisung des Arrays `%1` vollständig zu eliminieren (auch bekannt als "Skalarersetzung").

Im Vergleich zur Analyse von Objektfeldern, bei der der Zugriff auf Objektfelder trivial mithilfe von durch Inferenz abgeleiteten Typinformationen analysiert werden kann, wird die Array-Dimension nicht als Typinformation kodiert, und daher benötigen wir eine zusätzliche Analyse, um diese Informationen abzuleiten. `EscapeAnalysis` führt in diesem Moment zunächst einen zusätzlichen einfachen linearen Scan durch, um die Dimensionen der allokierten Arrays zu analysieren, bevor die Hauptanalyse-Routine gestartet wird, damit die nachfolgende Escape-Analyse die Operationen auf diesen Arrays präzise analysieren kann.

Allerdings ist eine so präzise "pro-Element" Alias-Analyse oft schwierig. Im Wesentlichen besteht die Hauptschwierigkeit darin, dass die Array-Dimension und der Index oft nicht konstant sind:

  * Schleifen erzeugen oft schleifenvariante, nicht konstante Array-Indizes.
  * (spezifisch für Vektoren) Die Größenänderung eines Arrays ändert die Array-Dimension und macht seine Konstantheit ungültig.

Lass uns diese Schwierigkeiten mit konkreten Beispielen besprechen.

Im folgenden Beispiel schlägt die `EscapeAnalysis` die präzise Alias-Analyse fehl, da der Index bei `Base.arrayset(false, %4, %8, %6)::Vector{Any}` nicht (trivially) konstant ist. Besonders `Any[nothing, nothing]` bildet eine Schleife und ruft diese `arrayset`-Operation in einer Schleife auf, wobei `%6` als ϕ-Knotenwert dargestellt wird (dessen Wert von der Kontrollflussabhängigkeit abhängt). Infolgedessen wird `ReturnEscape` sowohl auf `%23` (entsprechend `SafeRef(s)`) als auch auf `%25` (entsprechend `SafeRef(t)`) auferlegt, obwohl wir idealerweise möchten, dass es nur auf `%23` und nicht auf `%25` auferlegt wird:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[nothing, nothing]
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

Das nächste Beispiel veranschaulicht, wie das Ändern der Größe von Vektoren präzise Alias-Analysen erschwert. Die wesentliche Schwierigkeit besteht darin, dass die Dimension des zugewiesenen Arrays `%1` zunächst auf `0` initialisiert wird, sich jedoch durch die beiden `:jl_array_grow_end`-Aufrufe danach ändert. `EscapeAnalysis` gibt derzeit einfach die präzise Alias-Analyse auf, wann immer es auf Array-Größenänderungen stößt, und so wird `ReturnEscape` sowohl auf `%2` (entsprechend `SafeRef(s)`) als auch auf `%20` (entsprechend `SafeRef(t)`) auferlegt:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[]
    push!(ary, SafeRef(s))
    push!(ary, SafeRef(t))
    ary[1], length(ary)
end
```

Um diese Schwierigkeiten zu beheben, müssen wir sicherstellen, dass die Inferenz sich der Array-Dimensionen bewusst ist und die Array-Dimensionen auf flussabhängige Weise propagiert, sowie eine ansprechende Darstellung von schleifenvarianten Werten entwickeln.

`EscapeAnalysis` wechselt in diesem Moment schnell zu der ungenaueren Analyse, die keine präzisen Indexinformationen verfolgt, wenn die Array-Dimensionen oder Indizes trivialerweise nicht konstant sind. Der Wechsel kann natürlich als ein Gitter-Vereinigungsoperation der `EscapeInfo.AliasInfo`-Eigenschaft im Datenflussanalyse-Rahmen implementiert werden.

### [Exception Handling](@id EA-Exception-Handling)

Es wäre auch erwähnenswert, wie `EscapeAnalysis` mögliche Ausflüsse über Ausnahmen behandelt. Naiv scheint es ausreichend zu sein, die Ausflusinformationen, die auf das `:the_exception`-Objekt auferlegt werden, auf alle Werte zu propagieren, die in einem entsprechenden `try`-Block geworfen werden können. Es gibt jedoch tatsächlich mehrere andere Möglichkeiten, auf das Ausnahmeobjekt in Julia zuzugreifen, wie `Base.current_exceptions` und `rethrow`. Zum Beispiel muss die Ausflusanalyse den potenziellen Ausfluss von `r` im folgenden Beispiel berücksichtigen:

```@repl EAUtils
const GR = Ref{Any}();
@noinline function rethrow_escape!()
    try
        rethrow()
    catch err
        GR[] = err
    end
end;
get′(x) = isassigned(x) ? x[] : throw(x);

code_escapes() do
    r = Ref{String}()
    local t
    try
        t = get′(r)
    catch err
        t = typeof(err)   # `err` (which `r` aliases to) doesn't escape here
        rethrow_escape!() # but `r` escapes here
    end
    return t
end
```

Es erfordert eine globale Analyse, um korrekt über alle möglichen Ausnahmen über bestehende Ausnahme-Schnittstellen nachzudenken. Derzeit propagieren wir immer die oberste Auskunft über Ausnahmen an alle potenziell geworfenen Objekte konservativ, da eine solche zusätzliche Analyse möglicherweise nicht lohnenswert ist, da die Ausnahmebehandlung und der Fehlerpfad in der Regel nicht sehr leistungsempfindlich sein müssen und auch Optimierungen von Fehlerpfaden ohnehin sehr ineffektiv sein könnten, da sie oft sogar absichtlich "nicht optimiert" aus Latenzgründen sind.

`x::EscapeInfo`'s `x.ThrownEscape`-Eigenschaft zeichnet SSA-Anweisungen auf, bei denen `x` als Ausnahme geworfen werden kann. Mit diesen Informationen kann `EscapeAnalysis` mögliche Ausnahmen über Ausnahmen begrenzt nur auf die propagieren, die in jedem `try`-Bereich geworfen werden können:

```@repl EAUtils
result = code_escapes((String,String)) do s1, s2
    r1 = Ref(s1)
    r2 = Ref(s2)
    local ret
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    return s2
end
```

## Analysis Usage

`analyze_escapes` ist der Einstiegspunkt zur Analyse von Escape-Informationen von SSA-IR-Elementen.

Die meisten Optimierungen wie SROA (`sroa_pass!`) sind effektiver, wenn sie auf einen optimierten Quellcode angewendet werden, den der Inlining-Pass (`ssa_inlining_pass!`) vereinfacht hat, indem er inter-prozedurale Aufrufe aufgelöst und die aufgerufenen Quellen erweitert hat. Dementsprechend kann `analyze_escapes` auch IR nach dem Inlining analysieren und Fluchtinformationen sammeln, die für bestimmte speicherbezogene Optimierungen nützlich sind.

Allerdings können bestimmte Optimierungspässe wie Inlining, die Kontrollflüsse ändern und toten Code eliminieren, die inter-prozedurale Gültigkeit von Escape-Informationen beeinträchtigen. Insbesondere müssen wir, um inter-prozedural gültige Escape-Informationen zu sammeln, eine IR vor dem Inlining analysieren.

Aus diesem Grund kann `analyze_escapes` `IRCode` auf jeder Optimierungsstufe von Julia analysieren, und insbesondere soll es in den folgenden beiden Phasen verwendet werden:

  * `IPO EA`: Analysiere die IR vor dem Inlining, um einen IPO-gültigen Escape-Informationscache zu generieren.
  * `Local EA`: Analysiere Post-Inlining-IR, um lokal gültige Escape-Informationen zu sammeln.

Die durch `IPO EA` abgeleiteten Escape-Informationen werden in die Datenstruktur `ArgEscapeCache` umgewandelt und global zwischengespeichert. Durch das Übergeben eines geeigneten `get_escape_cache`-Callbacks an `analyze_escapes` kann die Escape-Analyse die Analysegenauigkeit verbessern, indem sie zwischengespeicherte inter-prozedurale Informationen von nicht-inlineden Aufrufern nutzt, die durch vorherige `IPO EA` abgeleitet wurden. Interessanterweise ist es auch gültig, die Escape-Informationen von `IPO EA` für die Typinferenz zu verwenden, z. B. kann die Inferenzgenauigkeit verbessert werden, indem `Const`/`PartialStruct`/`MustAlias` von veränderlichen Objekten gebildet werden.

```@docs
Core.Compiler.EscapeAnalysis.analyze_escapes
Core.Compiler.EscapeAnalysis.EscapeState
Core.Compiler.EscapeAnalysis.EscapeInfo
```

---

[^LatticeDesign]: Our type inference implementation takes the alternative approach, where each lattice property is represented by a special lattice element type object. It turns out that it started to complicate implementations of the lattice operations mainly because it often requires conversion rules between each lattice element type object. And we are working on [overhauling our type inference lattice implementation](https://github.com/JuliaLang/julia/pull/42596) with `EscapeInfo`-like lattice design.

[^MM02]: *A Graph-Free approach to Data-Flow Analysis*.      Markas Mohnen, 2002, April.      [https://api.semanticscholar.org/CorpusID:28519618](https://api.semanticscholar.org/CorpusID:28519618).

[^BackandForth]: Our type inference algorithm in contrast is implemented as a forward analysis, because type information usually flows from "definition" to "usage" and it is more natural and effective to propagate such information in a forward way.

[^Dynamism]: In some cases, however, object fields can't be analyzed precisely. For example, object may escape to somewhere `EscapeAnalysis` can't account for possible memory effects on it, or fields of the objects simply can't be known because of the lack of type information. In such cases `AliasInfo` property is raised to the topmost element within its own lattice order, and it causes succeeding field analysis to be conservative and escape information imposed on fields of an unanalyzable object to be propagated to the object itself.

[^JVM05]: *Escape Analysis in the Context of Dynamic Compilation and Deoptimization*.       Thomas Kotzmann and Hanspeter Mössenböck, 2005, June.       [https://dl.acm.org/doi/10.1145/1064979.1064996](https://dl.acm.org/doi/10.1145/1064979.1064996).

[^ArrayDimension]: Otherwise we will need yet another forward data-flow analysis on top of the escape analysis.
