# Fixing precompilation hangs due to open tasks or IO

In Julia 1.10 oder höher könnten Sie die folgende Nachricht sehen:

![Screenshot des Prekompilierungs-Hangs](./img/precompilation_hang.png)

Dies kann sich wiederholen. Wenn es weiterhin ohne Hinweise darauf, dass es sich von selbst lösen wird, wiederholt wird, haben Sie möglicherweise ein "Precompilation Hang", das behoben werden muss. Selbst wenn es vorübergehend ist, möchten Sie es möglicherweise beheben, damit die Benutzer nicht von dieser Warnung gestört werden. Diese Seite führt Sie durch die Analyse und Behebung solcher Probleme.

Wenn Sie den Rat befolgen und `Ctrl-C` drücken, könnten Sie sehen

```
^C Interrupted: Exiting precompilation...

  1 dependency had warnings during precompilation:
┌ Test1 [ac89d554-e2ba-40bc-bc5c-de68b658c982]
│  [pid 2745] waiting for IO to finish:
│   Handle type        uv_handle_t->data
│   timer              0x55580decd1e0->0x7f94c3a4c340
```

Diese Nachricht vermittelt zwei wichtige Informationen:

  * der Hang tritt während der Vorcompilierung von `Test1` auf, einer Abhängigkeit von `Test2` (dem Paket, das wir mit `using Test2` zu laden versuchten)
  * während der Vorcompilierung von `Test1` hat Julia ein `Timer`-Objekt erstellt (verwenden Sie `?Timer`, wenn Sie mit Timern nicht vertraut sind), das noch geöffnet ist; bis es geschlossen wird, ist der Prozess blockiert.

Wenn dies genug Hinweis für Sie ist, um herauszufinden, wie `timer = Timer(args...)` erstellt wird, ist eine gute Lösung, `wait(timer)` hinzuzufügen, wenn `timer` schließlich von selbst endet, oder `close(timer)`, wenn Sie es vor dem endgültigen `end` des Moduls zwangsweise schließen müssen.

Es gibt jedoch Fälle, die möglicherweise nicht so einfach sind. In der Regel ist es am besten, zunächst festzustellen, ob das Hängenbleiben auf den Code in Test1 oder auf eine der Abhängigkeiten von Test1 zurückzuführen ist:

  * Option 1: `Pkg.add("Aqua")` und verwenden Sie [`Aqua.test_persistent_tasks`](https://juliatesting.github.io/Aqua.jl/dev/#Aqua.test_persistent_tasks-Tuple{Base.PkgId}). Dies sollte Ihnen helfen, das Problem verursachende Paket zu identifizieren, nach dem die Anweisungen [below](@ref pchang_fix) befolgt werden sollten. Falls erforderlich, können Sie eine `PkgId` erstellen als `Base.PkgId(UUID("..."), "Test1")`, wobei `...` aus dem `uuid`-Eintrag in `Test1/Project.toml` stammt.
  * Option 2: Manuell die Quelle des Hängens diagnostizieren.

Um manuell zu diagnostizieren:

1. `Pkg.develop("Test1")`
2. Comment out all the code `include`d or defined in `Test1`, *except* the `using/import` statements.
3. Versuche erneut `using Test2` (oder sogar `using Test1`, falls das auch hängt)

Jetzt erreichen wir eine Gabelung: entweder

  * der Hang bleibt bestehen, was darauf hindeutet, dass es [due to one of your dependencies](@ref pchang_deps) ist.
  * der Hang verschwindet, was darauf hindeutet, dass es [due to something in your code](@ref pchang_fix) ist.

## [Diagnosing and fixing hangs due to a package dependency](@id pchang_deps)

Verwenden Sie eine binäre Suche, um die problematische Abhängigkeit zu identifizieren: Beginnen Sie damit, die Hälfte Ihrer Abhängigkeiten auszukommentieren. Wenn Sie die verantwortliche Hälfte isoliert haben, kommentieren Sie die Hälfte dieser Hälfte aus usw. (Sie müssen sie nicht aus dem Projekt entfernen, sondern nur die `using`-/`import`-Anweisungen auskommentieren.)

Sobald Sie einen Verdächtigen identifiziert haben (hier nennen wir ihn `ThePackageYouThinkIsCausingTheProblem`), versuchen Sie zunächst, dieses Paket vorzukompilieren. Wenn es auch während der Vorabkompilierung hängt, verfolgen Sie das Problem weiter rückwärts.

Es ist jedoch sehr wahrscheinlich, dass `ThePackageYouThinkIsCausingTheProblem` problemlos vorcompiliert wird. Das deutet darauf hin, dass es in der Funktion `ThePackageYouThinkIsCausingTheProblem.__init__` liegt, die während der Vorcompilierung von `ThePackageYouThinkIsCausingTheProblem` nicht ausgeführt wird, aber *doch* in jedem Paket, das `ThePackageYouThinkIsCausingTheProblem` lädt. Um diese Theorie zu testen, richten Sie ein minimales funktionierendes Beispiel (MWE) ein, etwas wie

```julia
(@v1.10) pkg> generate MWE
  Generating  project MWE:
    MWE\Project.toml
    MWE\src\MWE.jl
```

wo der Quellcode von `MWE.jl` ist

```julia
module MWE
using ThePackageYouThinkIsCausingTheProblem
end
```

und du hast `ThePackageYouThinkIsCausingTheProblem` zu den Abhängigkeiten von MWE hinzugefügt.

Wenn dieses MWE das Hängen reproduziert, haben Sie Ihren Übeltäter gefunden: `ThePackageYouThinkIsCausingTheProblem.__init__` muss das `Timer`-Objekt erstellen. Wenn das Timer-Objekt sicher `close`d werden kann, ist das eine gute Option. Andernfalls ist die häufigste Lösung, die Erstellung des Timers zu vermeiden, während *irgendein* Paket vorcompiliert wird: fügen Sie hinzu

```julia
ccall(:jl_generating_output, Cint, ()) == 1 && return nothing
```

als die erste Zeile von `ThePackageYouThinkIsCausingTheProblem.__init__`, und es wird vermieden, irgendwelche Initialisierungen in einem Julia-Prozess durchzuführen, dessen Zweck es ist, Pakete vorzukompilieren.

## [Fixing package code to avoid hangs](@id pchang_fix)

Durchsuchen Sie Ihr Paket nach suggestiven Wörtern (hier wie "Timer") und prüfen Sie, ob Sie identifizieren können, wo das Problem entsteht. Beachten Sie, dass eine *Definition* einer Methode wie

```julia
maketimer() = Timer(timer -> println("hi"), 0; interval=1)
```

ist an sich nicht problematisch: Es kann dieses Problem nur verursachen, wenn `maketimer` aufgerufen wird, während das Modul definiert wird. Dies könnte von einer Anweisung auf oberster Ebene wie folgt geschehen

```julia
const GLOBAL_TIMER = maketimer()
```

oder es könnte möglicherweise in einer [precompile workload](https://github.com/JuliaLang/PrecompileTools.jl) auftreten.

Wenn Sie Schwierigkeiten haben, die ursächlichen Zeilen zu identifizieren, ziehen Sie in Betracht, eine binäre Suche durchzuführen: Kommentieren Sie Abschnitte Ihres Pakets aus (oder `include`-Zeilen, um ganze Dateien auszuschließen), bis Sie das Problem im Umfang reduziert haben.
