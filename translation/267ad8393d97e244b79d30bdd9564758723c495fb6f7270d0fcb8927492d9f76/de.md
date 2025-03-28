# System Image Building

## [Building the Julia system image](@id Building-the-Julia-system-image)

Julia wird mit einem vorverarbeiteten Systembild geliefert, das die Inhalte des `Base`-Moduls enthält und `sys.ji` genannt wird. Diese Datei wird auch in eine gemeinsam genutzte Bibliothek namens `sys.{so,dll,dylib}` auf so vielen Plattformen wie möglich vorcompiliert, um erheblich verbesserte Startzeiten zu bieten. Auf Systemen, die nicht mit einer vorcompilierten Systembilddatei geliefert werden, kann eine solche aus den Quellcodedateien im `DATAROOTDIR/julia/base`-Ordner von Julia generiert werden.

Julia wird standardmäßig ihr System-Image auf der Hälfte der verfügbaren System-Threads generieren. Dies kann durch die Umgebungsvariable [`JULIA_IMAGE_THREADS`](@ref JULIA_IMAGE_THREADS) gesteuert werden.

Dieser Vorgang ist aus mehreren Gründen nützlich. Ein Benutzer kann:

  * Erstellen Sie ein vorcompiliertes Shared Library-System-Image auf einer Plattform, die mit einem solchen nicht ausgeliefert wurde, um die Startzeiten zu verbessern.
  * Ändern Sie `Base`, erstellen Sie das Systemabbild neu und verwenden Sie das neue `Base`, wenn Julia das nächste Mal gestartet wird.
  * Fügen Sie eine `userimg.jl`-Datei ein, die Pakete in das Systembild einfügt, wodurch ein Systembild erstellt wird, das Pakete in die Startumgebung eingebettet hat.

Die [`PackageCompiler.jl` package](https://github.com/JuliaLang/PackageCompiler.jl) enthält praktische Wrapper-Funktionen, um diesen Prozess zu automatisieren.

## [System image optimized for multiple microarchitectures](@id sysimg-multi-versioning)

Das Systembild kann gleichzeitig für mehrere CPU-Mikroarchitekturen unter derselben Befehlssatzarchitektur (ISA) kompiliert werden. Mehrere Versionen derselben Funktion können erstellt werden, wobei ein minimaler Dispatch-Punkt in gemeinsame Funktionen eingefügt wird, um von verschiedenen ISA-Erweiterungen oder anderen Mikroarchitekturmerkmalen zu profitieren. Die Version, die die beste Leistung bietet, wird zur Laufzeit automatisch basierend auf den verfügbaren CPU-Funktionen ausgewählt.

### Specifying multiple system image targets

Ein Multi-Mikroarchitektur-Systembild kann aktiviert werden, indem mehrere Ziele während der Systembildkompilierung übergeben werden. Dies kann entweder mit der [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) Make-Option oder mit der `-C` Befehlszeilenoption beim manuellen Ausführen des Kompilierungsbefehls erfolgen. Mehrere Ziele sind im Optionsstring durch `;` getrennt. Die Syntax für jedes Ziel besteht aus einem CPU-Namen, gefolgt von mehreren Funktionen, die durch `,` getrennt sind. Alle von LLVM unterstützten Funktionen werden unterstützt, und eine Funktion kann mit einem `-` Präfix deaktiviert werden. (`+` Präfix ist ebenfalls erlaubt und wird ignoriert, um mit der LLVM-Syntax konsistent zu sein). Darüber hinaus werden einige spezielle Funktionen unterstützt, um das Verhalten der Funktionsklonierung zu steuern.

!!! note
    Es ist gute Praxis, entweder `clone_all` oder `base(<n>)` für jedes Ziel außer dem ersten anzugeben. Dies macht deutlich, welche Ziele alle Funktionen geklont haben und welche Ziele auf anderen Zielen basieren. Wenn dies nicht getan wird, besteht das Standardverhalten darin, nicht jede Funktion zu klonen und die Funktionsdefinition des ersten Ziels als Fallback zu verwenden, wenn eine Funktion nicht geklont wird.


1. `clone_all`

    Standardmäßig werden nur Funktionen, die am wahrscheinlichsten von den Mikroarchitekturmerkmalen profitieren, geklont. Wenn jedoch `clone_all` für ein Ziel angegeben wird, werden **alle** Funktionen im Systemabbild für das Ziel geklont. Die negative Form `-clone_all` kann verwendet werden, um zu verhindern, dass die integrierte Heuristik alle Funktionen klont.
2. `basis(<n>)`

    Wo `<n>` ein Platzhalter für eine nicht-negative Zahl ist (z. B. `base(0)`, `base(1)`). Standardmäßig verwendet ein teilweise geklonter (d. h. nicht `clone_all`) Ziel Funktionen vom Standardziel (dem zuerst angegebenen), wenn eine Funktion nicht geklont ist. Dieses Verhalten kann geändert werden, indem ein anderes Basisziel mit der Option `base(<n>)` angegeben wird. Das `n`-te Ziel (0-basiert) wird als Basisziel anstelle des Standardziels (0. Ziel) verwendet. Das Basisziel muss entweder `0` oder ein anderes `clone_all`-Ziel sein. Die Angabe eines nicht-`clone_all`-Ziels als Basisziel führt zu einem Fehler.
3. `opt_size`

    Dies führt dazu, dass die Funktion für das Ziel optimiert wird, um die Größe zu minimieren, wenn es keinen signifikanten Einfluss auf die Laufzeitleistung gibt. Dies entspricht der `-Os` GCC- und Clang-Option.
4. `min_size`

    Dies führt dazu, dass die Funktion für das Ziel auf Größe optimiert wird, was erhebliche Auswirkungen auf die Laufzeitleistung haben könnte. Dies entspricht der Clang-Option `-Oz`.

Als Beispiel wird zum Zeitpunkt dieses Schreibens der folgende String bei der Erstellung der offiziellen `x86_64` Julia-Binärdateien verwendet, die von julialang.org heruntergeladen werden können:

```
generic;sandybridge,-xsaveopt,clone_all;haswell,-rdrnd,base(1)
```

Dies erstellt ein System-Image mit drei separaten Zielen; eines für einen generischen `x86_64` Prozessor, eines mit einer `sandybridge` ISA (die `xsaveopt` ausdrücklich ausschließt), das alle Funktionen explizit klont, und eines, das auf die `haswell` ISA abzielt, basierend auf der `sandybridge` sysimg-Version und ebenfalls `rdrnd` ausschließt. Wenn eine Julia-Implementierung das generierte sysimg lädt, wird sie den Host-Prozessor auf übereinstimmende CPU-Fähigkeitsflags überprüfen, um das höchste mögliche ISA-Niveau zu aktivieren. Beachten Sie, dass das Basismodell (`generic`) den `cx16` Befehl erfordert, der in einigen Virtualisierungssoftware deaktiviert ist und aktiviert werden muss, damit das `generic` Ziel geladen werden kann. Alternativ könnte ein sysimg mit dem Ziel `generic,-cx16` für größere Kompatibilität generiert werden, beachten Sie jedoch, dass dies in einigen Codes zu Leistungs- und Stabilitätsproblemen führen kann.

### Implementation overview

Dies ist eine kurze Übersicht über die verschiedenen Teile, die an der Implementierung beteiligt sind. Siehe Codekommentare für weitere Implementierungsdetails.

1. Systembildkompilierung

    Die Parsing- und Klonentscheidungen werden in `src/processor*` getroffen. Wir unterstützen derzeit das Klonen von Funktionen basierend auf der Anwesenheit von Schleifen, SIMD-Anweisungen oder anderen mathematischen Operationen (z. B. fastmath, fma, muladd). Diese Informationen werden an `src/llvm-multiversioning.cpp` weitergegeben, das das eigentliche Klonen durchführt. Neben dem Klonen und dem Einfügen von Dispatch-Slots (siehe Kommentare in `MultiVersioning::runOnModule`, wie dies geschieht) generiert der Pass auch Metadaten, damit die Laufzeit das System-Image korrekt laden und initialisieren kann. Eine detaillierte Beschreibung der Metadaten ist in `src/processor.h` verfügbar.
2. Systemabbild laden

    Das Laden und die Initialisierung des Systembildes erfolgen in `src/processor*` durch das Parsen der während der Erstellung des Systembildes gespeicherten Metadaten. Die Erkennung von Host-Funktionen und die Auswahlentscheidungen erfolgen in `src/processor_*.cpp` abhängig von der ISA. Die Zielauswahl bevorzugt eine exakte Übereinstimmung des CPU-Namens, eine größere Vektorregistergröße und eine größere Anzahl von Funktionen. Eine Übersicht über diesen Prozess befindet sich in `src/processor.cpp`.
