```@eval
io = IOBuffer()
release = isempty(VERSION.prerelease)
v = "$(VERSION.major).$(VERSION.minor)"
!release && (v = v*"-$(first(VERSION.prerelease))")
print(io, """
    # Julia $(v) Documentation

    Welcome to the documentation for Julia $(v).

    """)
if !release
    print(io,"""
        !!! warning "Work in progress!"
            This documentation is for an unreleased, in-development, version of Julia.
        """)
end
import Markdown
Markdown.parse(String(take!(io)))
```

Bitte lesen Sie die [release notes](NEWS.md), um zu sehen, was sich seit der letzten Veröffentlichung geändert hat.

```@eval
release = isempty(VERSION.prerelease)
file = release ? "julia-$(VERSION).pdf" :
       "julia-$(VERSION.major).$(VERSION.minor).$(VERSION.patch)-$(first(VERSION.prerelease)).pdf"
url = "https://raw.githubusercontent.com/JuliaLang/docs.julialang.org/assets/$(file)"
import Markdown
Markdown.parse("""
!!! note
    The documentation is also available in PDF format: [$file]($url).
""")
```

## [Important Links](@id man-important-links)

Unten finden Sie eine nicht erschöpfende Liste von Links, die nützlich sein werden, während Sie die Programmiersprache Julia lernen und verwenden.

  * [Julia Homepage](https://julialang.org)
  * [Download Julia](https://julialang.org/downloads/)
  * [Discussion forum](https://discourse.julialang.org)
  * [Julia YouTube](https://www.youtube.com/user/JuliaLanguage)
  * [Find Julia Packages](https://julialang.org/packages/)
  * [Learning Resources](https://julialang.org/learning/)
  * [Read and write blogs on Julia](https://forem.julialang.org)

## [Introduction](@id man-introduction)

Wissenschaftliches Rechnen hat traditionell die höchste Leistung erfordert, doch Fachleute haben weitgehend zu langsameren dynamischen Sprachen für die tägliche Arbeit gewechselt. Wir glauben, dass es viele gute Gründe gibt, dynamische Sprachen für diese Anwendungen zu bevorzugen, und wir erwarten nicht, dass ihre Nutzung abnimmt. Glücklicherweise ermöglichen moderne Sprachdesign- und Compiler-Techniken, den Leistungsnachteil größtenteils zu beseitigen und eine einzige Umgebung bereitzustellen, die sowohl produktiv genug für Prototyping als auch effizient genug für die Bereitstellung leistungsintensiver Anwendungen ist. Die Programmiersprache Julia erfüllt diese Rolle: Sie ist eine flexible dynamische Sprache, die für wissenschaftliches und numerisches Rechnen geeignet ist und eine Leistung bietet, die mit traditionellen statisch typisierten Sprachen vergleichbar ist.

Weil Julias Compiler sich von den Interpretern unterscheidet, die für Sprachen wie Python oder R verwendet werden, kann es sein, dass die Leistung von Julia zunächst unintuitiv erscheint. Wenn Sie feststellen, dass etwas langsam ist, empfehlen wir dringend, den Abschnitt [Performance Tips](@ref man-performance-tips) durchzulesen, bevor Sie etwas anderes versuchen. Sobald Sie verstehen, wie Julia funktioniert, ist es einfach, Code zu schreiben, der fast so schnell ist wie C.

## [Julia Compared to Other Languages](@id man-julia-compared-other-languages)

Julia bietet optionale Typisierung, multiple Dispatch und gute Leistung, die durch Typinferenz und [just-in-time (JIT) compilation](https://en.wikipedia.org/wiki/Just-in-time_compilation) (und [optional ahead-of-time compilation](https://github.com/JuliaLang/PackageCompiler.jl)), implementiert mit [LLVM](https://en.wikipedia.org/wiki/Low_Level_Virtual_Machine). Es ist multiparadigmatisch und kombiniert Merkmale der imperativen, funktionalen und objektorientierten Programmierung. Julia bietet Einfachheit und Ausdruckskraft für hochrangige numerische Berechnungen, ähnlich wie Sprachen wie R, MATLAB und Python, unterstützt jedoch auch allgemeine Programmierung. Um dies zu erreichen, baut Julia auf der Linie mathematischer Programmiersprachen auf, leiht sich jedoch auch viel von beliebten dynamischen Sprachen, einschließlich [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language)), [Perl](https://en.wikipedia.org/wiki/Perl_(programming_language)), [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), [Lua](https://en.wikipedia.org/wiki/Lua_(programming_language)) und [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)).

Die bedeutendsten Abweichungen von Julia im Vergleich zu typischen dynamischen Sprachen sind:

  * Die Kernsprache auferlegt sehr wenig; Julia Base und die Standardbibliothek sind in Julia selbst geschrieben, einschließlich primitiver Operationen wie Ganzzahl-Arithmetik.
  * Eine reiche Sprache von Typen zur Konstruktion und Beschreibung von Objekten, die auch optional zur Erstellung von Typdeklarationen verwendet werden kann.
  * Die Fähigkeit, das Verhalten von Funktionen über viele Kombinationen von Argumenttypen hinweg zu definieren, über [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch)
  * Automatische Generierung von effizientem, spezialisiertem Code für verschiedene Argumenttypen
  * Gute Leistung, die der von statisch kompilierten Sprachen wie C nahekommt.

Obwohl man manchmal von dynamischen Sprachen als "typlos" spricht, sind sie es definitiv nicht. Jedes Objekt, ob primitiv oder benutzerdefiniert, hat einen Typ. Das Fehlen von Typdeklarationen in den meisten dynamischen Sprachen bedeutet jedoch, dass man den Compiler nicht über die Typen von Werten informieren kann und oft nicht einmal explizit über Typen sprechen kann. In statischen Sprachen hingegen, während man – und normalerweise muss – Typen für den Compiler annotieren kann, existieren Typen nur zur Compile-Zeit und können zur Laufzeit nicht manipuliert oder ausgedrückt werden. In Julia sind Typen selbst Laufzeitobjekte und können auch verwendet werden, um Informationen an den Compiler zu übermitteln.

### [What Makes Julia, Julia?](@id man-what-makes-julia)

Während der Gelegenheitsprogrammierer Typen oder Mehrfachdispatch nicht explizit verwenden muss, sind sie die zentralen einheitlichen Merkmale von Julia: Funktionen werden für verschiedene Kombinationen von Argumenttypen definiert und durch Dispatching auf die spezifischste passende Definition angewendet. Dieses Modell passt gut zur mathematischen Programmierung, wo es unnatürlich ist, dass das erste Argument eine Operation "besitzt", wie es im traditionellen objektorientierten Dispatch der Fall ist. Operatoren sind einfach Funktionen mit spezieller Notation – um die Addition auf neue benutzerdefinierte Datentypen zu erweitern, definieren Sie neue Methoden für die `+`-Funktion. Vorhandener Code wird dann nahtlos auf die neuen Datentypen angewendet.

Teilweise aufgrund der Laufzeit-Typinferenz (unterstützt durch optionale Typannotationen) und teilweise wegen des starken Fokus auf Leistung von Anfang an, übertrifft Julias rechnerische Effizienz die anderer dynamischer Sprachen und rivalisiert sogar mit der von statisch kompilierten Sprachen. Bei großangelegten numerischen Problemen war Geschwindigkeit immer entscheidend, ist es weiterhin und wird es wahrscheinlich immer sein: Die Menge der verarbeiteten Daten hat in den letzten Jahrzehnten mühelos mit dem Gesetz von Moore Schritt gehalten.

### [Advantages of Julia](@id man-advantages-of-julia)

Julia zielt darauf ab, eine beispiellose Kombination aus Benutzerfreundlichkeit, Leistung und Effizienz in einer einzigen Sprache zu schaffen. Neben den oben genannten Vorteilen bietet Julia im Vergleich zu ähnlichen Systemen einige zusätzliche Vorteile:

  * Kostenlos und Open Source ([MIT licensed](https://github.com/JuliaLang/julia/blob/master/LICENSE.md))
  * Benutzerdefinierte Typen sind ebenso schnell und kompakt wie eingebaute Typen.
  * Kein Bedarf, den Code zur Leistungssteigerung zu vektorisieren; devektorisierter Code ist schnell.
  * Entwickelt für Parallelität und verteilte Berechnung
  * Leichte "grüne" Threads ([coroutines](https://en.wikipedia.org/wiki/Coroutine))
  * Unauffällig, aber leistungsstarkes Typsystem
  * Elegante und erweiterbare Konversionen und Promotionen für numerische und andere Typen
  * Effiziente Unterstützung für [Unicode](https://en.wikipedia.org/wiki/Unicode), einschließlich, aber nicht beschränkt auf [UTF-8](https://en.wikipedia.org/wiki/UTF-8)
  * Rufen Sie C-Funktionen direkt auf (keine Wrapper oder speziellen APIs erforderlich)
  * Mächtige shell-ähnliche Funktionen zur Verwaltung anderer Prozesse
  * Lisp-ähnliche Makros und andere Metaprogrammierungsfunktionen
