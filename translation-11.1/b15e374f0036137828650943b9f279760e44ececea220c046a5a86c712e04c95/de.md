# Reporting and analyzing crashes (segfaults)

Also haben Sie es geschafft, Julia zu brechen. Herzlichen Glückwunsch! Hier sind einige allgemeine Verfahren, die Sie bei häufigen Symptomen durchführen können, wenn etwas schiefgeht. Die Einbeziehung der Informationen aus diesen Debugging-Schritten kann den Entwicklern erheblich helfen, wenn sie einen Segfault nachverfolgen oder herausfinden, warum Ihr Skript langsamer als erwartet läuft.

Wenn Sie zu dieser Seite geleitet wurden, finden Sie das Symptom, das am besten zu dem passt, was Sie erleben, und folgen Sie den Anweisungen, um die angeforderten Debugging-Informationen zu generieren.  Tabelle der Symptome:

  * [Segfaults during bootstrap (`sysimg.jl`)](@ref)
  * [Segfaults when running a script](@ref)
  * [Errors during Julia startup](@ref)
  * [Other generic segfaults or unreachables reached](@ref)

## [Version/Environment info](@id dev-version-info)

Egal welcher Fehler auftritt, wir müssen immer wissen, welche Version von Julia Sie verwenden. Wenn Julia zum ersten Mal gestartet wird, wird ein Header mit einer Versionsnummer und einem Datum ausgegeben. Bitte fügen Sie auch die Ausgabe von `versioninfo()` (exportiert aus der [`InteractiveUtils`](@ref InteractiveUtils.versioninfo) Standardbibliothek) in jeden Bericht ein, den Sie erstellen:

```@repl
using InteractiveUtils
versioninfo()
```

## Segfaults during bootstrap (`sysimg.jl`)

Segfaults gegen Ende des `make`-Prozesses beim Erstellen von Julia sind ein häufiges Symptom dafür, dass etwas schiefgeht, während Julia den Code im `base/`-Ordner vorverarbeitet. Viele Faktoren können dazu führen, dass dieser Prozess unerwartet abbricht, jedoch liegt es oft an einem Fehler im C-Code-Teil von Julia, und muss daher typischerweise mit einem Debug-Build innerhalb von `gdb` debuggt werden. Explizit:

Erstellen Sie einen Debug-Build von Julia:

```
$ cd <julia_root>
$ make debug
```

Beachten Sie, dass dieser Prozess wahrscheinlich mit demselben Fehler wie ein normales `make`-Kommando fehlschlagen wird. Allerdings wird dadurch ein Debug-Executable erstellt, das `gdb` die benötigten Debugging-Symbole bietet, um genaue Rückverfolgungen zu erhalten. Führen Sie als Nächstes den Bootstrap-Prozess manuell innerhalb von `gdb` aus:

```
$ cd base/
$ gdb -x ../contrib/debug_bootstrap.gdb
```

Dies wird `gdb` starten, versuchen, den Bootstrap-Prozess mit dem Debug-Build von Julia auszuführen, und einen Backtrace ausgeben, falls (wenn) es zu einem Segfault kommt. Möglicherweise müssen Sie ein paar Mal `<enter>` drücken, um den vollständigen Backtrace zu erhalten. Erstellen Sie eine [gist](https://gist.github.com) mit dem Backtrace, der [version info](@ref dev-version-info) und allen anderen relevanten Informationen, die Sie sich vorstellen können, und öffnen Sie ein neues [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) auf Github mit einem Link zum Gist.

## Segfaults when running a script

Das Verfahren ist sehr ähnlich zu [Segfaults during bootstrap (`sysimg.jl`)](@ref). Erstellen Sie einen Debug-Build von Julia und führen Sie Ihr Skript innerhalb eines debugged Julia-Prozesses aus:

```
$ cd <julia_root>
$ make debug
$ gdb --args usr/bin/julia-debug <path_to_your_script>
```

Beachten Sie, dass `gdb` dort sitzen bleibt und auf Anweisungen wartet. Geben Sie `r` ein, um den Prozess auszuführen, und `bt`, um einen Backtrace zu erstellen, sobald er einen Segfault hat:

```
(gdb) r
Starting program: /home/sabae/src/julia/usr/bin/julia-debug ./test.jl
...
(gdb) bt
```

Erstellen Sie ein [gist](https://gist.github.com) mit dem Backtrace, der [version info](@ref dev-version-info), und allen anderen relevanten Informationen, die Sie sich vorstellen können, und öffnen Sie ein neues [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) auf Github mit einem Link zum Gist.

## Errors during Julia startup

Gelegentlich treten während des Startprozesses von Julia Fehler auf (insbesondere bei der Verwendung von Binärdistributionen im Gegensatz zum Kompilieren aus dem Quellcode), wie zum Beispiel:

```julia
$ julia
exec: error -5
```

Diese Fehler deuten typischerweise darauf hin, dass etwas sehr früh im Bootvorgang nicht richtig geladen wird, und unser bester Ansatz zur Bestimmung, was schiefgeht, ist die Verwendung externer Tools, um die Festplattenaktivität des `julia`-Prozesses zu überprüfen:

  * Auf Linux verwenden Sie `strace`:

    ```
    $ strace julia
    ```
  * Auf OSX verwenden Sie `dtruss`:

    ```
    $ dtruss -f julia
    ```

Erstellen Sie ein [gist](https://gist.github.com) mit der `strace`/ `dtruss` Ausgabe, der [version info](@ref dev-version-info), und allen anderen relevanten Informationen und öffnen Sie ein neues [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) auf Github mit einem Link zum Gist.

## Other generic segfaults or unreachables reached

Wie an anderer Stelle erwähnt, hat `julia` eine gute Integration mit `rr` zur Generierung von Traces; dies umfasst unter Linux die Möglichkeit, `julia` automatisch unter `rr` auszuführen und den Trace nach einem Absturz zu teilen. Dies kann beim Debuggen solcher Abstürze äußerst hilfreich sein und wird dringend empfohlen, wenn Absturzprobleme im JuliaLang/julia-Repo gemeldet werden. Um `julia` automatisch unter `rr` auszuführen, tun Sie Folgendes:

```julia
julia --bug-report=rr
```

Um den `rr`-Trace lokal zu generieren, aber nicht zu teilen, können Sie Folgendes tun:

```julia
julia --bug-report=rr-local
```

Beachten Sie, dass dies nur unter Linux funktioniert. Der Blogbeitrag zu [Time Travelling Bug Reporting](https://julialang.org/blog/2020/05/rr/) enthält viele weitere Details.

## Glossary

Einige Begriffe wurden in diesem Leitfaden als Abkürzungen verwendet:

  * `<julia_root>` bezieht sich auf das Stammverzeichnis des Julia-Quellbaums; z. B. sollte es Ordner wie `base`, `deps`, `src`, `test` usw. enthalten.....
