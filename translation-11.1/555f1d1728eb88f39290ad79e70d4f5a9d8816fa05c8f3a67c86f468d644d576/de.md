# External Profiler Support

Julia bietet explizite Unterstützung für einige externe Tracing-Profiler, mit denen Sie einen Überblick über das Ausführungsverhalten zur Laufzeit erhalten können.

Die derzeit unterstützten Profiler sind:

  * [Tracy](https://github.com/wolfpld/tracy)
  * [Intel VTune (ITTAPI)](https://github.com/intel/ittapi)

### Adding New Zones

Um neue Zonen hinzuzufügen, verwenden Sie das `JL_TIMING`-Makro. Sie finden zahlreiche Beispiele im gesamten Code, indem Sie nach `JL_TIMING` suchen. Um einen neuen Zonentyp hinzuzufügen, fügen Sie ihn zu `JL_TIMING_OWNERS` (und möglicherweise `JL_TIMING_EVENTS`) hinzu.

### Dynamically Enabling and Disabling Zones

Die [`JULIA_TIMING_SUBSYSTEMS`](@ref JULIA_TIMING_SUBSYSTEMS) Umgebungsvariable ermöglicht es Ihnen, Zonen für einen bestimmten Julia-Durchlauf zu aktivieren oder zu deaktivieren. Wenn Sie die Variable beispielsweise auf `+GC,-INFERENCE` setzen, werden die `GC`-Zonen aktiviert und die `INFERENCE`-Zonen deaktiviert.

## Tracy Profiler

[Tracy](https://github.com/wolfpld/tracy) ist ein flexibles Profiler, das optional mit Julia integriert werden kann.

Eine typische Tracy-Sitzung könnte folgendermaßen aussehen:

![Typische Tracy-Nutzung](tracy.png)

### Building Julia with Tracy

Um die Tracy-Integration zu aktivieren, bauen Sie Julia mit der zusätzlichen Option `WITH_TRACY=1` in der Datei `Make.user`.

### Installing the Tracy Profile Viewer

Der einfachste Weg, den Profilbetrachter zu erhalten, besteht darin, das Paket `TracyProfiler_jll` hinzuzufügen und den Profiler mit folgendem Befehl zu starten:

```julia
run(TracyProfiler_jll.tracy())
```

!!! note
    Unter macOS möchten Sie möglicherweise die Umgebungsvariable `TRACY_DPI_SCALE` auf `1.0` setzen, wenn die UI-Elemente im Profiler übermäßig groß erscheinen.


Um eine "headless" Instanz auszuführen, die die Spur auf der Festplatte speichert, verwenden Sie

```julia
run(`$(TracyProfiler_jll.capture()) -o mytracefile.tracy`)
```

stattdessen.

Für Informationen zur Verwendung der Tracy-Benutzeroberfläche siehe das Tracy-Handbuch.

### Profiling Julia with Tracy

Ein typischer Workflow zum Profiling von Julia mit Tracy umfasst das Starten von Julia mit:

```julia
JULIA_WAIT_FOR_TRACY=1 ./julia -e '...'
```

Die Umgebungsvariable stellt sicher, dass Julia wartet, bis es erfolgreich mit dem Tracy-Profiling-Tool verbunden ist, bevor die Ausführung fortgesetzt wird. Danach verwenden Sie die Tracy-Profiling-Benutzeroberfläche, klicken Sie auf `Connect`, und die Julia-Ausführung sollte fortgesetzt werden und das Profiling sollte beginnen.

### Profiling package precompilation with Tracy

Um den Prekompilierungsprozess eines Pakets zu profilieren, ist es am einfachsten, direkt in `Base.compilecache` mit dem Paket, das Sie vorkompilieren möchten, aufzurufen:

```julia
pkg = Base.identify_package("SparseArrays")
withenv("JULIA_WAIT_FOR_TRACY" => 1, "TRACY_PORT" => 9001) do
    Base.compilecache(pkg)
end
```

Hier verwenden wir einen benutzerdefinierten Port für Tracy, der es einfacher macht, den richtigen Client in der Tracy-Benutzeroberfläche zu finden, um eine Verbindung herzustellen.

### Adding metadata to zones

Die verschiedenen `jl_timing_show_*` und `jl_timing_printf` Funktionen können verwendet werden, um einen String (oder Strings) an eine Zone anzuhängen. Zum Beispiel zeigt die Trace-Zone für die Inferenz die Methodeninstanz, die gerade inferiert wird.

Die `TracyCZoneColor`-Funktion kann verwendet werden, um die Farbe einer bestimmten Zone festzulegen. Durchsuchen Sie den Code, um zu sehen, wie sie verwendet wird.

### Viewing Tracy files in your browser

Besuchen Sie https://topolarity.github.io/trace-viewer/ für einen (experimentellen) Web-Viewer für Tracy-Traces.

Sie können eine lokale `.tracy`-Datei öffnen oder eine URL aus dem Web bereitstellen (z. B. eine Datei in einem Github-Repo). Wenn Sie eine Trace-Datei aus dem Web laden, können Sie auch die Seiten-URL direkt mit anderen teilen, damit sie denselben Trace anzeigen können.

### Enabling stack trace samples

Um das Call-Stack-Sampling in Tracy zu aktivieren, bauen Sie Julia mit diesen Optionen in Ihrer `Make.user`-Datei:

```
WITH_TRACY := 1
WITH_TRACY_CALLSTACKS := 1
USE_BINARYBUILDER_LIBTRACYCLIENT := 0
```

Sie müssen möglicherweise auch `make -C deps clean-libtracyclient` ausführen, um einen erneuten Build von Tracy zu erzwingen.

Diese Funktion hat einen erheblichen Einfluss auf die Trace-Größe und den Profiling-Overhead, daher wird empfohlen, das Sampling des Call-Stapels, wenn möglich, deaktiviert zu lassen, insbesondere wenn Sie beabsichtigen, Ihre Trace-Dateien online zu teilen.

Beachten Sie, dass die Julia JIT-Laufzeit derzeit keine Integration für Tracys Symbolifizierung hat, sodass Julia-Funktionen in diesen Stack-Traces typischerweise unbekannt sind.

## Intel VTune (ITTAPI) Profiler

*Dieser Abschnitt muss noch geschrieben werden.*
