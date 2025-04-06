```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/NEWS.md"
```

# Julia v1.11 Release Notes

## New language features

  * Neuer `Memory`-Typ, der einen niedrigeren Container als Alternative zu `Array` bereitstellt. `Memory` hat weniger Overhead und einen schnelleren Konstruktor, was es zu einer guten Wahl für Situationen macht, die nicht alle Funktionen von `Array` benötigen (z. B. mehrere Dimensionen). Der Großteil des `Array`-Typs ist jetzt in Julia auf `Memory` implementiert, was zu erheblichen Geschwindigkeitssteigerungen für mehrere Funktionen (z. B. `push!`) sowie zu wartbarerem Code führt ([#51319](https://github.com/JuliaLang/julia/issues/51319)).
  * `public` is a new keyword. Symbols marked with `public` are considered public API. Symbols marked with `export` are now also treated as public API. The difference between `public` and `export` is that `public` names do not become available when `using` a package/module ([#50105](https://github.com/JuliaLang/julia/issues/50105)).
  * `ScopedValue` implementiert dynamischen Scope mit Vererbung über Aufgaben hinweg ([#50958](https://github.com/JuliaLang/julia/issues/50958)).
  * `Manifest.toml`-Dateien können jetzt im Format `Manifest-v{major}.{minor}.toml` umbenannt werden, um von der angegebenen Julia-Version bevorzugt ausgewählt zu werden. Das heißt, im selben Ordner würde eine `Manifest-v1.11.toml` von v1.11 verwendet werden und `Manifest.toml` von jeder anderen Julia-Version. Dies erleichtert die Verwaltung von Umgebungen für mehrere Julia-Versionen zur gleichen Zeit ([#43845](https://github.com/JuliaLang/julia/issues/43845)).
  * Unterstützung für Unicode 15.1 ([#51799](https://github.com/JuliaLang/julia/issues/51799)).

## Language changes

  * Während der Vorcompilierung werden `atexit`-Hooks jetzt vor dem Speichern der Ausgabedatei ausgeführt. Dies ermöglicht es den Benutzern, den Hintergrundstatus sicher abzubauen (wie das Schließen von `Timer`s und das Senden von Trennungsbenachrichtigungen an Herzschlagaufgaben) und andere Ressourcen zu bereinigen, wenn das Programm mit dem Beenden beginnen möchte.
  * Die Codeabdeckung und das Malloc-Tracking werden während der Vorabkompilierungsphase des Pakets nicht mehr generiert. Darüber hinaus werden in diesen Modi jetzt pkgimage-Caches für Pakete verwendet, die nicht verfolgt werden. Das bedeutet, dass die Abdeckungstests (der Standard für `julia-actions/julia-runtest`) standardmäßig pkgimage-Caches für alle anderen Pakete als das getestete Paket verwenden, was wahrscheinlich schnellere Testausführungen zur Folge hat ([#52123](https://github.com/JuliaLang/julia/issues/52123)).
  * Das Festlegen eines Pfades in `JULIA_DEPOT_PATH` führt jetzt dazu, dass leere Zeichenfolgen erweitert werden, um das Standardbenutzerdepot ([#51448](https://github.com/JuliaLang/julia/issues/51448)) zu omittieren.
  * Precompilation-Cache-Dateien sind jetzt umsetzbar, und ihre Gültigkeit wird jetzt durch einen Inhalts-Hash ihrer Quelldateien anstelle ihres `mtime` verifiziert ([#49866](https://github.com/JuliaLang/julia/issues/49866)).
  * Erweiterungen können jetzt von anderen Erweiterungen abhängen, wenn ihre Trigger alle Trigger einer Erweiterung enthalten, von der sie abhängen möchten (+ mindestens einen weiteren Trigger). Erweiterungen, die diese Anforderung nicht erfüllen, ist es jetzt untersagt, `Base.get_extension` während der Vorabkompilierung zu verwenden, um Erweiterungszyklen zu verhindern [#55557](https://github.com/JuliaLang/julia/issues/55557).

## Compiler/Runtime improvements

  * Aktualisierte GC-Heuristiken zur Zählung der zugewiesenen Seiten anstelle einzelner Objekte ([#50144](https://github.com/JuliaLang/julia/issues/50144)).
  * Added support for annotating `Base.@assume_effects` on code blocks ([#52400](https://github.com/JuliaLang/julia/issues/52400)).

## Command-line option changes

  * Der Einstiegspunkt für Julia wurde auf `Main.main(args)` standardisiert. Dies muss ausdrücklich mit dem `@main`-Makro aktiviert werden (siehe die Dokumentation für weitere Details). Wenn dies aktiviert ist und `julia` aufgerufen wird, um ein Skript oder einen Ausdruck auszuführen (d.h. mit `julia script.jl` oder `julia -e expr`), wird `julia` anschließend automatisch die Funktion `Main.main` ausführen. Dies soll die Arbeitsabläufe von Skripten und Kompilierungen vereinheitlichen, bei denen das Laden von Code im Compiler und die Ausführung von `Main.main` im resultierenden ausführbaren Programm stattfinden kann. Für die interaktive Nutzung gibt es keinen semantischen Unterschied zwischen der Definition einer `main`-Funktion und der direkten Ausführung des Codes am Ende des Skripts ([#50974](https://github.com/JuliaLang/julia/issues/50974)).
  * Die `--compiled-modules` und `--pkgimages` Flags können jetzt auf `existing` gesetzt werden, was dazu führt, dass Julia vorhandene Cache-Dateien in Betracht zieht, jedoch keine neuen erstellt ([#50586](https://github.com/JuliaLang/julia/issues/50586), [#52573](https://github.com/JuliaLang/julia/issues/52573)).
  * Das `--project` Argument akzeptiert jetzt `@script`, um einen Pfad zu einem Verzeichnis mit einer Project.toml relativ zur übergebenen Skriptdatei anzugeben. `--project=@script/foo` für das Unterverzeichnis `foo`. Wenn kein Pfad angegeben wird (d.h. `--project=@script`), dann wird (wie bei `--project=@.`) das Verzeichnis und seine übergeordneten Verzeichnisse nach einer Project.toml durchsucht ([#50864](https://github.com/JuliaLang/julia/issues/50864) und [#53352](https://github.com/JuliaLang/julia/issues/53352))

## Multi-threading changes

  * `Threads.@threads` now supports the `:greedy` scheduler, intended for non-uniform workloads ([#52096](https://github.com/JuliaLang/julia/issues/52096)).
  * A new public (but unexported) struct `Base.Lockable{T, L<:AbstractLock}` makes it easy to bundle a resource and its lock together ([#52898](https://github.com/JuliaLang/julia/issues/52898)).

## Build system changes

  * Es gibt ein neues `Makefile`, um Julia und LLVM unter Verwendung der Strategien für profilgesteuerte und Linkzeitoptimierungen (PGO und LTO) zu erstellen. Siehe `contrib/pgo-lto/Makefile` ([#45641](https://github.com/JuliaLang/julia/issues/45641)).

## New library functions

  * Drei neue Typen rund um die Idee von Text mit "Annotationen" (`Pair{Symbol, Any}`-Einträgen, z.B. `:lang => "en"` oder `:face => :magenta`). Diese Annotationen werden bei Operationen (z.B. String-Verkettung mit `*`) erhalten, wenn möglich.

      * `AnnotatedString` ist ein neuer `AbstractString`-Typ. Er umschließt einen zugrunde liegenden String und ermöglicht es, Anmerkungen an Regionen des Strings anzuhängen. Dieser Typ wird in der neuen `StyledStrings`-Standardbibliothek umfassend verwendet, um Styling-Informationen zu halten.
      * `AnnotatedChar` ist ein neuer `AbstractChar`-Typ. Er umschließt ein anderes Zeichen und hält eine Liste von Annotationen, die darauf zutreffen.
      * `AnnotatedIOBuffer` ist ein neuer `IO`-Typ, der ein `IOBuffer` nachahmt, aber spezialisierte `read`/`write`-Methoden für annotierte Inhalte hat. Dies kann sowohl als eine Art "String-Builder" als auch als Verbindung zwischen annotierten und nicht annotierten Inhalten betrachtet werden.
  * `in!(x, s::AbstractSet)` gibt zurück, ob `x` in `s` ist, und fügt `x` in `s` ein, wenn nicht ([#45156](https://github.com/JuliaLang/julia/issues/45156), [#51636](https://github.com/JuliaLang/julia/issues/51636)).
  * Die neue `Libc.mkfifo`-Funktion umschließt die `mkfifo`-C-Funktion auf Unix-Plattformen ([#34587](https://github.com/JuliaLang/julia/issues/34587)).
  * `logrange(start, stop; length)` makes a range of constant ratio, instead of constant step ([#39071](https://github.com/JuliaLang/julia/issues/39071))
  * `copyuntil(out, io, delim)` und `copyline(out, io)` kopieren Daten in einen `out::IO`-Stream ([#48273](https://github.com/JuliaLang/julia/issues/48273)).
  * `eachrsplit(string, pattern)` iteriert über die aufgeteilten Teilstrings von rechts nach links ([#51646](https://github.com/JuliaLang/julia/issues/51646)).
  * `Sys.username()` kann verwendet werden, um den Benutzernamen des aktuellen Benutzers zurückzugeben ([#51897](https://github.com/JuliaLang/julia/issues/51897)).
  * `Sys.isreadable(), Sys.iswritable()` können verwendet werden, um zu überprüfen, ob der aktuelle Benutzer Zugriffsberechtigungen hat, die das Lesen und Schreiben jeweils erlauben. ([#53320](https://github.com/JuliaLang/julia/issues/53320)).
  * `GC.logging_enabled()` kann verwendet werden, um zu testen, ob das GC-Logging über `GC.enable_logging` aktiviert wurde ([#51647](https://github.com/JuliaLang/julia/issues/51647)).
  * `IdSet` wird jetzt von Base exportiert und als öffentlich betrachtet ([#53262](https://github.com/JuliaLang/julia/issues/53262)).
  * `@time` berichtet jetzt über die Anzahl von Sperrkonflikten, bei denen ein `ReentrantLock` warten musste, sowie ein neues Makro `@lock_conflicts`, das diese Anzahl zurückgibt ([#52883](https://github.com/JuliaLang/julia/issues/52883)).
  * Das neue Makro `Base.Cartesian.@ncallkw` ist analog zu `Base.Cartesian.@ncall`, ermöglicht jedoch das Hinzufügen von Schlüsselwortargumenten zum Funktionsaufruf ([#51501](https://github.com/JuliaLang/julia/issues/51501)).
  * Neue Funktion `Docs.hasdoc(module, symbol)` zeigt an, ob ein Name eine Docstring hat ([#52139](https://github.com/JuliaLang/julia/issues/52139)).
  * Neue Funktion `Docs.undocumented_names(module)` gibt die undokumentierten öffentlichen Namen eines Moduls zurück ([#52413](https://github.com/JuliaLang/julia/issues/52413)).

## New library features

  * `invmod(n, T)` wobei `T` ein nativer Ganzzahltyp ist, berechnet jetzt die modulare Inverse von `n` im modularen Ganzzahlring, den `T` definiert ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `invmod(n)` ist eine Abkürzung für `invmod(n, typeof(n))` für native Ganzzahltypen ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `replace(string, pattern...)` unterstützt jetzt ein optionales `IO`-Argument, um die Ausgabe an einen Stream zu schreiben, anstatt einen String zurückzugeben ([#48625](https://github.com/JuliaLang/julia/issues/48625)).
  * New methods `allequal(f, itr)` and `allunique(f, itr)` taking a predicate function ([#47679](https://github.com/JuliaLang/julia/issues/47679)).
  * `sizehint!(s, n)` unterstützt jetzt ein optionales `shrink`-Argument, um das Schrumpfen zu deaktivieren ([#51929](https://github.com/JuliaLang/julia/issues/51929)).
  * Passing an `IOBuffer` as a stdout argument for `Process` spawn now works as expected, synchronized with `wait` or `success`, so a `Base.BufferStream` is no longer required there for correctness to avoid data races ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * Nachdem ein Prozess beendet ist, wird `closewrite` nicht mehr automatisch auf dem übergebenen Stream aufgerufen. Rufen Sie stattdessen `wait` auf dem Prozess auf, um sicherzustellen, dass der Inhalt vollständig geschrieben ist, und rufen Sie dann `closewrite` manuell auf, um Datenrennen zu vermeiden, oder verwenden Sie die Callback-Form von `open`, um all dies automatisch zu handhaben ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * `@timed` gibt jetzt zusätzlich die vergangene Kompilierungs- und Rekompilierungszeit zurück ([#52889](https://github.com/JuliaLang/julia/issues/52889)).
  * `filter` kann jetzt auf ein `NamedTuple` wirken ([#50795](https://github.com/JuliaLang/julia/issues/50795)).
  * `Iterators.cycle(iter, n)` durchläuft `iter` eine feste Anzahl von Malen, anstatt für immer ([#47354](https://github.com/JuliaLang/julia/issues/47354)).
  * `zero(::AbstractArray)` now applies recursively, so `zero([[1,2],[3,4,5]])` now produces the additive identity `[[0,0],[0,0,0]]` rather than erroring ([#38064](https://github.com/JuliaLang/julia/issues/38064)).
  * `include_dependency(path; track_content=true)` ermöglicht den Wechsel von der Verwendung von `mtime` zu Hashing der Prekompilierungsabhängigkeit, um die Relokalisierbarkeit von Prekompilierungs-Caches wiederherzustellen ([#51798](https://github.com/JuliaLang/julia/issues/51798)).

## Standard library changes

  * Die Fallback-Methode `write(::IO, ::AbstractArray)` rief zuvor rekursiv `write` für jedes Element auf, schreibt jetzt jedoch die In-Memory-Darstellung jedes Wertes. Zum Beispiel schreibt `write(io, 'a':'b')` jetzt 4 Bytes für jedes Zeichen, anstatt die UTF-8-Darstellung jedes Zeichens zu schreiben. Das neue Format ist mit dem von `Array` verwendeten kompatibel, was es ermöglicht, `read!` zu verwenden, um die Daten zurückzubekommen ([#42593](https://github.com/JuliaLang/julia/issues/42593)).
  * Es ist nicht möglich, `length` für zustandsbehaftete Iteratoren auf eine allgemein konsistente Weise zu definieren. Das Potenzial für stillschweigend falsche Ergebnisse für `Stateful`-Iteratoren wird durch das Löschen der `length(::Stateful)`-Methode angesprochen. Der letzte Typparameter von `Stateful` ist ebenfalls verschwunden. Problem: ([#47790](https://github.com/JuliaLang/julia/issues/47790)), PR: ([#51747](https://github.com/JuliaLang/julia/issues/51747)).

#### Package Manager

  * Es ist jetzt möglich, "Quellen" für Pakete in einem `[sources]`-Abschnitt in Project.toml anzugeben. Dies kann verwendet werden, um nicht registrierte normale oder Testabhängigkeiten hinzuzufügen.
  * Pkg befolgt jetzt die `[compat]`-Grenzen für `julia` und gibt einen Fehler aus, wenn die Version der laufenden Julia-Binärdatei nicht mit den Grenzen in `Project.toml` übereinstimmt. Pkg hat diese Kompatibilität immer beachtet, wenn es um Registry-Pakete ging. Diese Änderung betrifft hauptsächlich lokale Pakete.
  * `pkg> add` und `Pkg.add` fügen jetzt Kompatibilitätseinträge für neue direkte Abhängigkeiten hinzu, wenn die aktive Umgebung ein Paket ist (eine `name` und `uuid`-Eintragung hat).
  * Abhängigkeiten können jetzt direkt als schwache Abhängigkeiten oder Extras über die `pkg> add --weak/extra Foo` oder `Pkg.add("Foo", target=:weakdeps/:extras)` Formen hinzugefügt werden.

#### StyledStrings

  * Eine neue Standardbibliothek zur umfassenderen und strukturierten Handhabung von Styling ([#49586](https://github.com/JuliaLang/julia/issues/49586)).
  * Die neue `Faces`-Struktur dient als Container für Informationen zur Textgestaltung (denken Sie an Schriftart sowie Farbe und Dekoration) und bietet ein Framework, das einen bequemen, erweiterbaren (über `addface!`) und anpassbaren (mit der `Faces.toml` des Benutzers und `loadfaces!`) Ansatz für gestaltete Inhalte bietet ([#49586](https://github.com/JuliaLang/julia/issues/49586)).
  * Das neue `@styled_str` String-Makro bietet eine bequeme Möglichkeit, ein `AnnotatedString` mit verschiedenen Schriftarten oder anderen Attributen zu erstellen ([#49586](https://github.com/JuliaLang/julia/issues/49586)).

#### Libdl

  * Ein neuer `LazyLibrary`-Typ wird aus `Libdl` exportiert, um beim Erstellen von verketteten faulen Bibliotheksladungen verwendet zu werden, hauptsächlich zur Verwendung innerhalb von JLLs ([#50074](https://github.com/JuliaLang/julia/issues/50074)).

#### LinearAlgebra

  * `cbrt(::AbstractMatrix{<:Real})` ist jetzt definiert und gibt die reellwertigen Matrixwürzel von reellwertigen Matrizen zurück ([#50661](https://github.com/JuliaLang/julia/issues/50661)).
  * `eigvals/eigen(A, bunchkaufman(B))` und `eigvals/eigen(A, lu(B))`, die die Bunchkaufman (LDL) und LU-Zerlegung von `B` nutzen, berechnen jetzt effizient die verallgemeinerten Eigenwerte (`eigen`: und Eigenvektoren) von `A` und `B`. Hinweis: Das zweite Argument ist die Ausgabe von `bunchkaufman` oder `lu` ([#50471](https://github.com/JuliaLang/julia/issues/50471)).
  * Es gibt jetzt einen spezialisierten Dispatch für `eigvals/eigen(::Hermitian{<:Tridiagonal})`, der eine Ähnlichkeitstransformation durchführt, um eine reelle symmetrische tridiagonale Matrix zu erstellen, und diese mit den LAPACK-Routinen löst ([#49546](https://github.com/JuliaLang/julia/issues/49546)).
  * Strukturierte Matrizen behalten jetzt entweder die Achsen des Elternteils (für `Symmetrisch`/`Hermitesch`/`AbstractTriangular`/`Obere Hessenberg`) oder die der Hauptdiagonale (für bandierte Matrizen) ([#52480](https://github.com/JuliaLang/julia/issues/52480)).
  * `bunchkaufman` und `bunchkaufman!` funktionieren jetzt für jeden `AbstractFloat`, `Rational` und deren komplexe Varianten. `bunchkaufman` unterstützt jetzt `Integer`-Typen, indem eine interne Umwandlung in `Rational{BigInt}` vorgenommen wird. Eine neue Funktion `inertia` wurde hinzugefügt, die die Inertie des diagonalen Faktors berechnet, der durch das `BunchKaufman`-Faktorisierungsobjekt einer reellen symmetrischen oder hermiteschen Matrix gegeben ist. Für komplexe symmetrische Matrizen berechnet `inertia` nur die Anzahl der Null-Eigenwerte des diagonalen Faktors ([#51487](https://github.com/JuliaLang/julia/issues/51487)).
  * Packages that specialize matrix-matrix `mul!` with a method signature of the form `mul!(::AbstractMatrix, ::MyMatrix, ::AbstractMatrix, ::Number, ::Number)` no longer encounter method ambiguities when interacting with `LinearAlgebra`. Previously, ambiguities used to arise when multiplying a `MyMatrix` with a structured matrix type provided by LinearAlgebra, such as `AbstractTriangular`, which used to necessitate additional methods to resolve such ambiguities. Similar sources of ambiguities have also been removed for matrix-vector `mul!` operations ([#52837](https://github.com/JuliaLang/julia/issues/52837)).
  * `lu` and `issuccess(::LU)` now accept an `allowsingular` keyword argument. When set to `true`, a valid factorization with rank-deficient U factor will be treated as success instead of throwing an error. Such factorizations are now shown by printing the factors together with a "rank-deficient" note rather than printing a "Failed Factorization" message ([#52957](https://github.com/JuliaLang/julia/issues/52957)).

#### Random

  * `rand` unterstützt jetzt das Sampling über `Tuple`-Typen ([#35856](https://github.com/JuliaLang/julia/issues/35856), [#50251](https://github.com/JuliaLang/julia/issues/50251)).
  * `rand` unterstützt jetzt das Sampling über `Pair`-Typen ([#28705](https://github.com/JuliaLang/julia/issues/28705)).
  * Beim Seed von RNGs, die von `Random` bereitgestellt werden, können jetzt negative Ganzzahl-Seed verwendet werden ([#51416](https://github.com/JuliaLang/julia/issues/51416)).
  * Seedbare Zufallszahlengeneratoren aus `Random` können jetzt mit einem String gesät werden, z.B. `seed!(rng, "a random seed")` ([#51527](https://github.com/JuliaLang/julia/issues/51527)).

#### REPL

  * Tab-Vervollständigungs-Hinweise werden jetzt in hellerer Schrift angezeigt, während Sie im REPL tippen. Um dies zu deaktivieren, setzen Sie `Base.active_repl.options.hint_tab_completes = false` interaktiv oder in startup.jl:

    ```
    if VERSION >= v"1.11.0-0"
      atreplinit() do repl
          repl.options.hint_tab_completes = false
      end
    end
    ```

    ([#51229](https://github.com/JuliaLang/julia/issues/51229)).
  * Meta-M mit einem leeren Prompt schaltet jetzt das kontextuelle Modul zwischen dem vorherigen Nicht-Haupt-Kontextmodul und dem Hauptmodul um, sodass das Hin- und Herwechseln einfach ist ([#51616](https://github.com/JuliaLang/julia/issues/51616), [#52670](https://github.com/JuliaLang/julia/issues/52670)).

#### Dates

Die undocumented Funktion `adjust` wird nicht mehr exportiert, ist aber jetzt dokumentiert ([#53092](https://github.com/JuliaLang/julia/issues/53092)).

#### Statistics

  * Statistik ist jetzt eine erweiterbare Standardbibliothek ([#46501](https://github.com/JuliaLang/julia/issues/46501)).

#### Distributed

  * `pmap` verwendet jetzt standardmäßig einen `CachingPool` ([#33892](https://github.com/JuliaLang/julia/issues/33892)).

## Deprecated or removed

  * `Base.map`, `Iterators.map` und `foreach` haben ihre Methoden mit einem einzelnen Argument verloren ([#52631](https://github.com/JuliaLang/julia/issues/52631)).

## External dependencies

  * Die libuv-Bibliothek wurde von der Version v1.44.2 auf v1.48.0 aktualisiert ([#49937](https://github.com/JuliaLang/julia/issues/49937)).
  * `tput` wird nicht mehr aufgerufen, um die Terminalfähigkeiten zu überprüfen; es wurde durch einen reinen Julia terminfo-Parser ersetzt ([#50797](https://github.com/JuliaLang/julia/issues/50797)).
  * Die Terminal-Informationsdatenbank, `terminfo`, wird jetzt standardmäßig mitgeliefert, was eine bessere REPL-Benutzererfahrung bietet, wenn `terminfo` nicht auf dem System verfügbar ist. Julia kann ohne das Mitliefern der Datenbank gebaut werden, indem die Makefile-Option `WITH_TERMINFO=0` verwendet wird. ([#55411](https://github.com/JuliaLang/julia/issues/55411))

## Tooling Improvements

  * CI führt jetzt eine begrenzte automatische Rechtschreibfehlererkennung bei allen PRs durch. Wenn Sie einen PR mit einem fehlerhaften Rechtschreibfehler-CI-Check zusammenführen, werden die gemeldeten Rechtschreibfehler in zukünftigen CI-Durchläufen bei PRs, die dieselben Dateien bearbeiten, automatisch ignoriert ([#51704](https://github.com/JuliaLang/julia/issues/51704)).
