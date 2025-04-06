# [Workflow Tips](@id man-workflow-tips)

Hier sind einige Tipps für die effiziente Arbeit mit Julia.

## REPL-based workflow

Wie bereits in [The Julia REPL](@ref) ausgeführt, bietet Julias REPL umfangreiche Funktionen, die einen effizienten interaktiven Workflow erleichtern. Hier sind einige Tipps, die Ihr Erlebnis an der Kommandozeile weiter verbessern könnten.

### A basic editor/REPL workflow

Die grundlegendsten Julia-Workflows beinhalten die Verwendung eines Texteditors in Verbindung mit der `julia`-Befehlszeile.

Erstellen Sie eine Datei mit dem Namen `Tmp.jl` und fügen Sie Folgendes ein:

```julia
module Tmp

say_hello() = println("Hello!")

# Your other definitions here

end # module

using .Tmp
```

Dann starten Sie im selben Verzeichnis die Julia REPL (mit dem Befehl `julia`). Führen Sie die neue Datei wie folgt aus:

```
julia> include("Tmp.jl")

julia> Tmp.say_hello()
Hello!
```

Erforschen Sie Ideen im REPL. Speichern Sie gute Ideen in `Tmp.jl`. Um die Datei nach der Änderung erneut zu laden, verwenden Sie einfach `include` erneut.

Der Schlüssel oben ist, dass Ihr Code in einem Modul gekapselt ist. Das ermöglicht es Ihnen, `struct`-Definitionen zu bearbeiten und Methoden zu entfernen, ohne Julia neu zu starten.

(Erläuterung: `struct`s können nach der Definition nicht bearbeitet werden, noch können Methoden gelöscht werden. Aber Sie *können* die Definition eines Moduls überschreiben, was wir tun, wenn wir `include("Tmp.jl")` erneut verwenden).

Darüber hinaus schützt die Kapselung von Code in einem Modul davor, von vorherigen Zuständen im REPL beeinflusst zu werden, was Sie vor schwer zu erkennenden Fehlern schützt.

## Browser-based workflow

Es gibt einige Möglichkeiten, mit Julia in einem Browser zu interagieren:

  * Verwendung von Pluto-Notebooks über [Pluto.jl](https://github.com/fonsp/Pluto.jl)
  * Verwendung von Jupyter-Notebooks über [IJulia.jl](https://github.com/JuliaLang/IJulia.jl)

## Revise-based workflows

Egal, ob Sie sich im REPL oder in IJulia befinden, können Sie Ihre Entwicklungserfahrung typischerweise mit [Revise](https://github.com/timholy/Revise.jl) verbessern. Es ist üblich, Revise so zu konfigurieren, dass es jedes Mal startet, wenn Julia gestartet wird, gemäß den Anweisungen in [Revise documentation](https://timholy.github.io/Revise.jl/stable/). Nach der Konfiguration wird Revise Änderungen an Dateien in allen geladenen Modulen und an allen Dateien, die mit `includet` in das REPL geladen werden (aber nicht mit plain `include`), verfolgen; Sie können dann die Dateien bearbeiten und die Änderungen treten in Kraft, ohne Ihre Julia-Sitzung neu zu starten. Ein standardmäßiger Workflow ähnelt dem oben beschriebenen REPL-basierten Workflow, mit den folgenden Modifikationen:

1. Legen Sie Ihren Code in ein Modul an einem Ort in Ihrem Ladepfad ab. Es gibt mehrere Optionen, um dies zu erreichen, von denen zwei empfohlene Optionen sind:

      * Für langfristige Projekte verwenden Sie [PkgTemplates](https://github.com/invenia/PkgTemplates.jl):

        ```julia
        using PkgTemplates
        t = Template()
        t("MyPkg")
        ```

        Dies erstellt ein leeres Paket, `"MyPkg"`, in Ihrem `.julia/dev` Verzeichnis. Beachten Sie, dass PkgTemplates Ihnen ermöglicht, viele verschiedene Optionen über seinen `Template`-Konstruktor zu steuern.

        In Schritt 2 unten, bearbeiten Sie `MyPkg/src/MyPkg.jl`, um den Quellcode zu ändern, und `MyPkg/test/runtests.jl` für die Tests.
      * Für "Wegwerf"-Projekte können Sie jeglichen Reinigungsaufwand vermeiden, indem Sie Ihre Arbeit in Ihrem temporären Verzeichnis (z. B. `/tmp`) durchführen.

        Navigieren Sie zu Ihrem temporären Verzeichnis und starten Sie Julia, dann tun Sie Folgendes:

        ```julia-repl
        pkg> generate MyPkg            # type ] to enter pkg mode
        julia> push!(LOAD_PATH, pwd())   # hit backspace to exit pkg mode
        ```

        Wenn Sie Ihre Julia-Sitzung neu starten, müssen Sie diesen Befehl zur Modifizierung von `LOAD_PATH` erneut ausführen.

        In Schritt 2 unten, bearbeiten Sie `MyPkg/src/MyPkg.jl`, um den Quellcode zu ändern, und erstellen Sie eine beliebige Testdatei Ihrer Wahl.
2. Entwickeln Sie Ihr Paket

    *Bevor* Sie irgendeinen Code laden, stellen Sie sicher, dass Sie Revise ausführen: sagen Sie `using Revise` oder folgen Sie der Dokumentation, um es automatisch auszuführen.

    Navigieren Sie dann zu dem Verzeichnis, das Ihre Testdatei enthält (hier angenommen, dass es sich um `"runtests.jl"` handelt), und führen Sie Folgendes aus:

    ```julia-repl
    julia> using MyPkg

    julia> include("runtests.jl")
    ```

    Sie können den Code in MyPkg in Ihrem Editor iterativ ändern und die Tests mit `include("runtests.jl")` erneut ausführen. In der Regel sollten Sie Ihre Julia-Sitzung nicht neu starten müssen, um die Änderungen wirksam werden zu lassen (mit Ausnahme einiger [limitations](https://timholy.github.io/Revise.jl/stable/limitations/)).
