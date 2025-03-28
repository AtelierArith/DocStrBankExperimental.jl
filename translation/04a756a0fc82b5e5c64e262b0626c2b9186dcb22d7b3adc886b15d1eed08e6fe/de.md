# [Getting Started](@id man-getting-started)

Die Installation von Julia ist unkompliziert, egal ob Sie vorcompilierte Binärdateien verwenden oder aus dem Quellcode kompilieren. Laden Sie Julia herunter und installieren Sie es, indem Sie die Anweisungen unter [https://julialang.org/downloads/](https://julialang.org/downloads/) befolgen.

Wenn Sie von einer der folgenden Sprachen zu Julia kommen, sollten Sie mit dem Abschnitt über bemerkenswerte Unterschiede beginnen: [MATLAB](@ref Noteworthy-differences-from-MATLAB), [R](@ref Noteworthy-differences-from-R), [Python](@ref Noteworthy-differences-from-Python), [C/C++](@ref Noteworthy-differences-from-C/C) oder [Common Lisp](@ref Noteworthy-differences-from-Common-Lisp). Dies wird Ihnen helfen, einige häufige Fallstricke zu vermeiden, da Julia sich in vielen subtilen Aspekten von diesen Sprachen unterscheidet.

Der einfachste Weg, Julia zu lernen und zu experimentieren, besteht darin, eine interaktive Sitzung (auch bekannt als Read-Eval-Print-Loop oder "REPL") zu starten, indem Sie die Julia-Ausführungsdatei doppelt anklicken oder `julia` von der Befehlszeile aus ausführen:

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia> 1 + 2\n3\n\njulia> ans\n3\n```")
```

Um die interaktive Sitzung zu beenden, geben Sie `CTRL-D` ein (drücken Sie die Steuerungstaste/`^` zusammen mit der `d`-Taste) oder geben Sie `exit()` ein. Wenn `julia` im interaktiven Modus ausgeführt wird, wird ein Banner angezeigt und der Benutzer zur Eingabe aufgefordert. Sobald der Benutzer einen vollständigen Ausdruck eingegeben hat, wie z.B. `1 + 2`, und die Eingabetaste drückt, wertet die interaktive Sitzung den Ausdruck aus und zeigt seinen Wert an. Wenn ein Ausdruck in einer interaktiven Sitzung mit einem nachgestellten Semikolon eingegeben wird, wird sein Wert nicht angezeigt. Die Variable `ans` ist an den Wert des zuletzt ausgewerteten Ausdrucks gebunden, unabhängig davon, ob er angezeigt wird oder nicht. Die `ans`-Variable ist nur in interaktiven Sitzungen gebunden, nicht wenn Julia-Code auf andere Weise ausgeführt wird.

Um Ausdrücke, die in einer Quelldatei `file.jl` geschrieben sind, auszuwerten, schreiben Sie `include("file.jl")`.

Um Code in einer Datei nicht-interaktiv auszuführen, können Sie ihn als erstes Argument an den `julia`-Befehl übergeben:

```
$ julia script.jl
```

Sie können zusätzliche Argumente an Julia und an Ihr Programm `script.jl` übergeben. Eine detaillierte Liste aller verfügbaren Optionen finden Sie unter [Command-line Interface](@ref cli).

## Resources

Eine kuratierte Liste nützlicher Lernressourcen, die neuen Benutzern den Einstieg erleichtern, finden Sie auf der [learning](https://julialang.org/learning/)-Seite der Haupt-Julia-Website.

Sie können die REPL als Lernressource nutzen, indem Sie in den Hilfemodus wechseln. Wechseln Sie in den Hilfemodus, indem Sie `?` an einer leeren `julia>`-Eingabeaufforderung drücken, bevor Sie etwas anderes eingeben. Das Eingeben eines Schlüsselworts im Hilfemodus ruft die Dokumentation dafür ab, zusammen mit Beispielen. Ähnlich verhält es sich mit den meisten Funktionen oder anderen Objekten, die Sie möglicherweise antreffen!

```
help?> begin
search: begin disable_sigint reenable_sigint

  begin

  begin...end denotes a block of code.
```

Wenn du bereits ein wenig über Julia weißt, möchtest du vielleicht einen Blick auf [Performance Tips](@ref man-performance-tips) und [Workflow Tips](@ref man-workflow-tips) werfen.
