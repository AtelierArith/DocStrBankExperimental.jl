# Custom LLVM Passes

Julia hat eine Reihe von benutzerdefinierten LLVM-Pässen. Im Großen und Ganzen können sie in Pässe unterteilt werden, die ausgeführt werden müssen, um die Semantik von Julia aufrechtzuerhalten, und Pässe, die die Semantik von Julia nutzen, um LLVM IR zu optimieren.

## Semantic Passes

Diese Pässe werden verwendet, um LLVM IR in Code zu transformieren, der auf einer CPU ausgeführt werden kann. Ihr Hauptzweck besteht darin, einfacheren IR zu ermöglichen, der von der Codegenerierung ausgegeben wird, was dann anderen LLVM-Pässen ermöglicht, gängige Muster zu optimieren.

### CPUFeatures

  * Dateiname: `llvm-cpufeatures.cpp`
  * Klassenname: `CPUFeaturesPass`
  * Opt-Name: `Modul(CPUFeatures)`

Dieser Pass senkt das `julia.cpu.have_fma.(f32|f64)` Intrinsic auf entweder wahr oder falsch, abhängig von der Zielarchitektur und den Zielmerkmalen, die in der Funktion vorhanden sind. Dieses Intrinsic wird oft verwendet, um zu bestimmen, ob die Verwendung von Algorithmen, die von schnellen [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add) Operationen abhängt, besser ist als die Verwendung von Standardalgorithmen, die nicht von solchen Anweisungen abhängen.

### DemoteFloat16

  * Dateiname: `llvm-demote-float16.cpp`
  * Klassenname: `DemoteFloat16Pass`
  * Opt-Name `function(DemoteFloat16)`

Dieser Pass ersetzt [float16](https://en.wikipedia.org/wiki/Half-precision_floating-point_format) Operationen durch float32 Operationen auf Architekturen, die nativ keine float16 Operationen unterstützen. Dies geschieht durch das Einfügen von `fpext` und `fptrunc` Anweisungen um jede float16 Operation. Auf Architekturen, die native float16 Operationen unterstützen, ist dieser Pass ein No-Op.

### LateGCLowering

  * Dateiname: `llvm-late-gc-lowering.cpp`
  * Klassenname: `LateLowerGCPass`
  * Opt-Name: `function(LateLowerGCFrame)`

Dieser Pass führt den Großteil der GC-Routing-Arbeiten durch, die erforderlich sind, um Zeiger zwischen GC-Sicherheitsstellen zu verfolgen. Er senkt auch mehrere Intrinsiken auf ihre entsprechenden Instruktionsübersetzungen ab und darf die zuvor festgelegten nicht-integralen Invarianten verletzen (`pointer_from_objref` wird hier auf eine `ptrtoint`-Instruktion abgesenkt). Dieser Pass benötigt typischerweise die meiste Zeit von allen benutzerdefinierten Julia-Pässen, aufgrund seines Datenflussalgorithmus, um die Anzahl der Objekte, die an einer Sicherheitsstelle lebendig sind, zu minimieren.

### FinalGCLowering

  * Dateiname: `llvm-final-gc-lowering.cpp`
  * Klassenname: `FinalLowerGCPass`
  * Opt-Name: `module(FinalLowerGC)`

Dieser Pass senkt einige letzte Intrinsiken auf ihre endgültige Form, die Funktionen in der `libjulia`-Bibliothek anvisiert. Die Trennung von `LateGCLowering` ermöglicht es anderen Backends (GPU-Kompilierung), ihre eigenen benutzerdefinierten Absenkungen für diese Intrinsiken bereitzustellen, wodurch die Julia-Pipeline auch auf diesen Backends verwendet werden kann.

### LowerHandlers

  * Dateiname: `llvm-lower-handlers.cpp`
  * Klassenname: `LowerExcHandlersPass`
  * Opt-Name: `function(LowerExcHandlers)`

Dieser Pass senkt die Ausnahmbehandlungsintrinsiken in Aufrufe von Laufzeitfunktionen, die tatsächlich beim Umgang mit Ausnahmen aufgerufen werden.

### RemoveNI

  * Dateiname: `llvm-remove-ni.cpp`
  * Klassenname: `RemoveNIPass`
  * Opt-Name: `Modul(RemoveNI)`

Dieser Pass entfernt die nicht-integralen Adressräume aus dem Datalayout-String des Moduls. Dies ermöglicht es dem Backend, Julias benutzerdefinierte Adressräume direkt in Maschinencode zu übersetzen, ohne eine kostspielige Umgestaltung jeder Zeigeroperation auf Adressraum 0.

### SIMDLoop

  * Dateiname: `llvm-simdloop.cpp`
  * Klassenname: `LowerSIMDLoopPass`
  * Opt-Name: `loop(LowerSIMDLoop)`

Dieser Pass fungiert als der Haupttreiber der `@simd`-Annotation. Der Codegenerator fügt ein `!llvm.loopid`-Marker am Rücksprung eines Loops ein, den dieser Pass verwendet, um Schleifen zu identifizieren, die ursprünglich mit `@simd` markiert wurden. Anschließend sucht dieser Pass nach einer Kette von Gleitkommaoperationen, die eine Reduktion bilden, und fügt die `contract`- und `reassoc`-Schnellmathematik-Flags hinzu, um die Wiederassoziation (und damit die Vektorisierung) zu ermöglichen. Dieser Pass bewahrt weder Schleifeninformationen noch die Korrektheit der Inferenz, sodass er die Julia-Semantik auf überraschende Weise verletzen kann. Wenn die Schleife auch mit `ivdep` annotiert war, markiert der Pass die Schleife als ohne Schleifenabhängigkeiten (das resultierende Verhalten ist undefiniert, wenn die Benutzerannotation falsch war oder auf die falsche Schleife angewendet wird).

### LowerPTLS

  * Dateiname: `llvm-ptls.cpp`
  * Klassenname: `LowerPTLSPass`
  * Opt-Name: `module(LowerPTLSPass)`

Dieser Pass senkt thread-lokale Julia-Intrinsiken auf Assemblieranweisungen. Julia verlässt sich auf thread-lokalen Speicher für die Garbage Collection und die Planung von Multithreading-Aufgaben. Beim Kompilieren von Code für Systembilder und Paketbilder ersetzt dieser Pass Aufrufe von Intrinsiken durch Ladevorgänge von globalen Variablen, die zur Ladezeit initialisiert werden.

Wenn die Codegenerierung eine Funktion mit einem `swiftself`-Argument und einer Aufrufkonvention erzeugt, geht dieser Pass davon aus, dass das `swiftself`-Argument der pgcstack ist und ersetzt die Intrinsics durch dieses Argument. Dies führt zu Geschwindigkeitsverbesserungen auf Architekturen, die langsame thread-lokale Speicherzugriffe haben.

### RemoveAddrspaces

  * Dateiname: `llvm-remove-addrspaces.cpp`
  * Klassenname: `RemoveAddrspacesPass`
  * Opt-Name: `modul(EntferneAddrspaces)`

Dieser Pass benennt Zeiger in einem Adressraum in einen anderen Adressraum um. Dies wird verwendet, um Julia-spezifische Adressräume aus LLVM IR zu entfernen.

### RemoveJuliaAddrspaces

  * Dateiname: `llvm-remove-addrspaces.cpp`
  * Klassenname: `RemoveJuliaAddrspacesPass`
  * Opt-Name: `module(RemoveJuliaAddrspaces)`

Dieser Pass entfernt Julia-spezifische Adressräume aus LLVM IR. Er wird hauptsächlich verwendet, um LLVM IR in einem weniger überladenen Format anzuzeigen. Intern wird er auf dem RemoveAddrspaces-Pass implementiert.

### Multiversioning

  * Dateiname: `llvm-multiversioning.cpp`
  * Klassenname: `MultiVersioningPass`
  * Opt Name: `modul(JuliaMultiVersionierung)`

Dieser Pass führt Modifikationen an einem Modul durch, um Funktionen zu erstellen, die für die Ausführung auf verschiedenen Architekturen optimiert sind (siehe sysimg.md und pkgimg.md für weitere Details). Implementierungstechnisch klont er Funktionen und wendet verschiedene zielarchitekturspezifische Attribute auf sie an, um dem Optimierer zu ermöglichen, fortschrittliche Funktionen wie Vektorisierung und Instruktionsplanung für diese Plattform zu nutzen. Er erstellt auch eine Infrastruktur, um dem Julia-Bildladeprogramm zu ermöglichen, die geeignete Version der Funktion auszuwählen, die basierend auf der Architektur, auf der der Loader läuft, aufgerufen werden soll. Die zielarchitekturspezifischen Attribute werden durch das `julia.mv.specs` Modul-Flag gesteuert, das während der Kompilierung aus der [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) Umgebungsvariable abgeleitet wird. Der Pass muss auch aktiviert werden, indem ein `julia.mv.enable` Modul-Flag mit einem Wert von 1 bereitgestellt wird.

!!! warning
    Die Verwendung von `llvmcall` mit Multiversionierung ist gefährlich. `llvmcall` ermöglicht den Zugriff auf Funktionen, die normalerweise nicht über die Julia-APIs verfügbar sind und daher in der Regel nicht auf allen Architekturen verfügbar sind. Wenn die Multiversionierung aktiviert ist und die Codegenerierung für eine Zielarchitektur angefordert wird, die die von einem `llvmcall`-Ausdruck benötigte Funktion nicht unterstützt, wird LLVM wahrscheinlich einen Fehler ausgeben, wahrscheinlich mit einem Abbruch und der Nachricht `LLVM ERROR: Do not know how to split the result of this operator!`.


### GCInvariantVerifier

  * Dateiname: `llvm-gc-invariant-verifier.cpp`
  * Klassenname: `GCInvariantVerifierPass`
  * Opt Name: `Modul(GCInvariantVerifier)`

Dieser Pass wird verwendet, um Julias Invarianten über LLVM IR zu überprüfen. Dazu gehören Dinge wie die Nichtexistenz von `ptrtoint` in Julias [non-integral address spaces](https://llvm.org/docs/LangRef.html#non-integral-pointer-type) [^nislides] und die Existenz von nur gesegneten `addrspacecast`-Anweisungen (Tracked -> Derived, 0 -> Tracked usw.). Es führt keine Transformationen am IR durch.

[^nislides]: https://llvm.org/devmtg/2015-02/slides/chisnall-pointers-not-int.pdf

## Optimization Passes

Diese Pässe werden verwendet, um Transformationen an LLVM IR durchzuführen, die LLVM selbst nicht ausführen wird, z. B. die Weitergabe von Fast-Math-Flags, Escape-Analyse und Optimierungen an Julia-spezifischen internen Funktionen. Sie nutzen das Wissen über Julias Semantik, um diese Optimierungen durchzuführen.

### CombineMulAdd

  * Dateiname: `llvm-muladd.cpp`
  * Klassenname: `CombineMulAddPass`
  * Opt-Name: `function(CombineMulAdd)`

Dieser Pass dient dazu, die besondere Kombination eines regulären `fmul` mit einem schnellen `fadd` in einen Vertrags-`fmul` mit einem schnellen `fadd` zu optimieren. Dies wird später vom Backend in eine [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add)-Anweisung optimiert, die deutlich schnellere Operationen auf Kosten von mehr [unpredictable semantics](https://simonbyrne.github.io/notes/fastmath/) bieten kann.

!!! note
    Diese Optimierung tritt nur auf, wenn der `fmul` eine einzige Verwendung hat, die die schnelle `fadd` ist.


### AllocOpt

  * Dateiname: `llvm-alloc-opt.cpp`
  * Klassenname: `AllocOptPass`
  * Opt-Name: `function(AllocOpt)`

Julia hat nicht das Konzept eines Programmstapels als Ort zur Zuweisung von veränderlichen Objekten. Das Zuweisen von Objekten auf dem Stapel verringert jedoch den GC-Druck und ist entscheidend für die GPU-Kompilierung. Daher führt `AllocOpt` eine Umwandlung von Heap- zu Stapelobjekten durch, die es beweisen kann, dass sie nicht [escape](https://en.wikipedia.org/wiki/Escape_analysis) die aktuelle Funktion verlassen. Es führt auch eine Reihe anderer Optimierungen bei Zuweisungen durch, wie das Entfernen von Zuweisungen, die niemals verwendet werden, das Optimieren von typeof-Aufrufen für frisch zugewiesene Objekte und das Entfernen von Zuweisungen, die sofort überschrieben werden. Die Implementierung der Fluchtanalyse befindet sich in `llvm-alloc-helpers.cpp`. Derzeit verwendet dieser Pass keine Informationen aus `EscapeAnalysis.jl`, obwohl sich das in Zukunft ändern könnte.

### PropagateJuliaAddrspaces

  * Dateiname: `llvm-propagate-addrspaces.cpp`
  * Klassenname: `PropagateJuliaAddrspacesPass`
  * Opt-Name: `function(PropagateJuliaAddrspaces)`

Dieser Pass wird verwendet, um Julia-spezifische Adressräume durch Operationen auf Zeigern zu propagieren. LLVM darf durch Optimierungen keine addrspacecast-Anweisungen einführen oder entfernen, daher wirkt dieser Pass, um redundante addrspace-Casts zu eliminieren, indem er Operationen durch ihre Entsprechungen in einem Julia-Adressraum ersetzt. Für weitere Informationen zu Julias Adressräumen siehe (TODO Link zu llvm.md).

### JuliaLICM

  * Dateiname: `llvm-julia-licm.cpp`
  * Klassenname: `JuliaLICMPass`
  * Opt-Name: `loop(JuliaLICM)`

Dieser Pass wird verwendet, um Julia-spezifische Intrinsiken aus Schleifen zu heben. Insbesondere führt er die folgenden Transformationen durch:

1. Hebe `gc_preserve_begin` und senke `gc_preserve_end` aus Schleifen heraus, wenn die bewahrten Objekte schleifeninvariant sind.

    1. Da Objekte, die innerhalb einer Schleife erhalten bleiben, wahrscheinlich für die Dauer der Schleife erhalten bleiben, kann diese Transformation die Anzahl der `gc_preserve_begin`/`gc_preserve_end`-Paare im IR reduzieren. Dies erleichtert es dem `LateLowerGCPass`, zu identifizieren, wo bestimmte Objekte erhalten bleiben.
2. Hebe Schreibbarrieren mit invarianten Objekten

    1. Hier nehmen wir an, dass es nur zwei Generationen gibt, zu denen ein Objekt gehören kann. Angesichts dessen muss eine Schreibsperre nur einmal für jedes Paar desselben Objekts ausgeführt werden. Daher können wir Schreibsperren aus Schleifen herausheben, wenn das zu beschreibende Objekt schleifeninvariant ist.
3. Heben Sie Zuweisungen aus Schleifen heraus, wenn sie die Schleife nicht verlassen.

    1. Wir verwenden hier eine sehr konservative Definition von Escape, die dieselbe ist wie die, die in `AllocOptPass` verwendet wird. Diese Transformation kann die Anzahl der Allokationen im IR reduzieren, selbst wenn eine Allokation die Funktion vollständig verlässt.

!!! note
    Dieser Pass ist erforderlich, um LLVMs [MemorySSA](https://llvm.org/docs/MemorySSA.html) ([Short Video](https://www.youtube.com/watch?v=bdxWmryoHak), [Longer Video](https://www.youtube.com/watch?v=1e5y6WDbXCQ)) und [ScalarEvolution](https://baziotis.cs.illinois.edu/compilers/introduction-to-scalar-evolution.html) ([Newer Slides](https://llvm.org/devmtg/2018-04/slides/Absar-ScalarEvolution.pdf) [Older Slides](https://llvm.org/devmtg/2009-10/ScalarEvolutionAndLoopOptimization.pdf)) Analysen zu erhalten.

