# [Package Images](@id pkgimages)

Das Julia-Paket `images` bietet Objekt- (Native-Code-) Caches für Julia-Pakete. Sie sind ähnlich wie Julias [system image](@ref dev-sysimg) und unterstützen viele der gleichen Funktionen. Tatsächlich ist das zugrunde liegende Serialisierungsformat dasselbe, und das System-Image ist das Basis-Image, gegen das die Paket-Images erstellt werden.

## High-level overview

Paketbilder sind gemeinsam genutzte Bibliotheken, die sowohl Code als auch Daten enthalten. Wie `.ji`-Cache-Dateien werden sie pro Paket generiert. Der Datenteil enthält sowohl globale Daten (globale Variablen im Paket) als auch die notwendigen Metadaten darüber, welche Methoden und Typen vom Paket definiert sind. Der Codeabschnitt enthält native Objekte, die die endgültige Ausgabe von Julias LLVM-basiertem Compiler zwischenspeichern.

Die Befehlszeilenoption `--pkgimages=no` kann verwendet werden, um das Objekt-Caching für diese Sitzung auszuschalten. Beachten Sie, dass dies bedeutet, dass Cache-Dateien wahrscheinlich neu generiert werden müssen. Siehe [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@ref JULIA_MAX_NUM_PRECOMPILE_FILES) für die obere Grenze der Varianten, die Julia standardmäßig cached.

!!! note
    Während die Paketbilder sich als native Shared Libraries präsentieren, sind sie nur eine Annäherung daran. Sie können nicht von einem nativen Programm aus mit ihnen verlinken, und sie müssen aus Julia geladen werden.


## Linking

Da die Paketbilder nativen Code enthalten, müssen wir einen Linker über sie ausführen, bevor wir sie verwenden können. Sie können die Umgebungsvariable [`JULIA_VERBOSE_LINKING`](@ref JULIA_VERBOSE_LINKING) auf `true` setzen, um den Verlinkungsprozess der Paketbilder ausführlich zu gestalten.

Darüber hinaus können wir nicht davon ausgehen, dass der Benutzer einen funktionierenden Systemlinker installiert hat. Daher wird Julia mit LLD, dem LLVM-Linker, ausgeliefert, um ein funktionierendes Erlebnis direkt nach der Installation zu bieten. In `base/linking.jl` implementieren wir eine eingeschränkte Schnittstelle, um Paketbilder auf allen unterstützten Plattformen verlinken zu können.

### Quirks

Trotz der Tatsache, dass LLD ein plattformübergreifender Linker ist, bietet er keine konsistente Schnittstelle über die Plattformen hinweg. Darüber hinaus ist er dafür gedacht, von `clang` oder einem anderen Compiler-Treiber verwendet zu werden, weshalb wir einige der Logik aus `llvm-project/clang/lib/Driver/ToolChains` neu implementieren. Glücklicherweise kann man `lld -flavor` verwenden, um lld auf die richtige Plattform einzustellen.

#### Windows

Um den Umgang mit `link.exe` zu vermeiden, verwenden wir `-flavor gnu`, wodurch `lld` effektiv zu einem Cross-Linker aus einer mingw32-Umgebung wird. Windows-DLLs müssen eine `_DllMainCRTStartup`-Funktion enthalten, und um unsere Abhängigkeit von mingw32-Bibliotheken zu minimieren, fügen wir selbst eine Stub-Definition ein.

#### MacOS

Dynamische Bibliotheken auf macOS müssen gegen `-lSystem` verlinken. In den neuesten macOS-Versionen ist `-lSystem` nur verfügbar, wenn Xcode installiert ist. Zu diesem Zweck verlinken wir mit `-undefined dynamic_lookup`.

## [Package images optimized for multiple microarchitectures](@id pkgimgs-multi-versioning)

Ähnlich wie [multi-versioning](@ref sysimg-multi-versioning) für Systembilder unterstützen Paketbilder die Mehrfachversionierung. Wenn Sie sich in einer heterogenen Umgebung mit einem einheitlichen Cache befinden, können Sie die Umgebungsvariable `JULIA_CPU_TARGET=generic` setzen, um die Objekt-Caches mehrmals zu versionieren.

## Flags that impact package image creation and selection

Dies sind die Julia-Befehlszeilenflags, die die Auswahl des Caches beeinflussen. Paketbilder, die mit unterschiedlichen Flags erstellt wurden, werden abgelehnt.

  * `-g`, `--debug-info`: Exakte Übereinstimmung erforderlich, da es die Codegenerierung ändert.
  * `--check-bounds`: Exakte Übereinstimmung erforderlich, da es die Codegenerierung ändert.
  * `--inline`: Exakte Übereinstimmung erforderlich, da sie die Codegenerierung ändert.
  * `--pkgimages`: Um das Ausführen ohne aktivierte Objekt-Caching zu ermöglichen.
  * `-O`, `--optimize`: Paketbilder, die für ein niedrigeres Optimierungsniveau generiert wurden, ablehnen, aber das Laden von Bildern mit höheren Optimierungsniveaus zulassen.
