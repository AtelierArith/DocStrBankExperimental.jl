# Working with LLVM

Dies ist kein Ersatz für die LLVM-Dokumentation, sondern eine Sammlung von Tipps für die Arbeit mit LLVM für Julia.

## Overview of Julia to LLVM Interface

Julia verknüpft standardmäßig dynamisch mit LLVM. Bauen Sie mit `USE_LLVM_SHLIB=0`, um statisch zu verknüpfen.

Der Code zum Senken des Julia AST zu LLVM IR oder zur direkten Interpretation befindet sich im Verzeichnis `src/`.

| File                             | Description                                                        |
|:-------------------------------- |:------------------------------------------------------------------ |
| `aotcompile.cpp`                 | Compiler C-interface entry and object file emission                |
| `builtins.c`                     | Builtin functions                                                  |
| `ccall.cpp`                      | Lowering [`ccall`](@ref)                                           |
| `cgutils.cpp`                    | Lowering utilities, notably for array and tuple accesses           |
| `codegen.cpp`                    | Top-level of code generation, pass list, lowering builtins         |
| `debuginfo.cpp`                  | Tracks debug information for JIT code                              |
| `disasm.cpp`                     | Handles native object file and JIT code diassembly                 |
| `gf.c`                           | Generic functions                                                  |
| `intrinsics.cpp`                 | Lowering intrinsics                                                |
| `jitlayers.cpp`                  | JIT-specific code, ORC compilation layers/utilities                |
| `llvm-alloc-helpers.cpp`         | Julia-specific escape analysis                                     |
| `llvm-alloc-opt.cpp`             | Custom LLVM pass to demote heap allocations to the stack           |
| `llvm-cpufeatures.cpp`           | Custom LLVM pass to lower CPU-based functions (e.g. haveFMA)       |
| `llvm-demote-float16.cpp`        | Custom LLVM pass to lower 16b float ops to 32b float ops           |
| `llvm-final-gc-lowering.cpp`     | Custom LLVM pass to lower GC calls to their final form             |
| `llvm-gc-invariant-verifier.cpp` | Custom LLVM pass to verify Julia GC invariants                     |
| `llvm-julia-licm.cpp`            | Custom LLVM pass to hoist/sink Julia-specific intrinsics           |
| `llvm-late-gc-lowering.cpp`      | Custom LLVM pass to root GC-tracked values                         |
| `llvm-lower-handlers.cpp`        | Custom LLVM pass to lower try-catch blocks                         |
| `llvm-muladd.cpp`                | Custom LLVM pass for fast-match FMA                                |
| `llvm-multiversioning.cpp`       | Custom LLVM pass to generate sysimg code on multiple architectures |
| `llvm-propagate-addrspaces.cpp`  | Custom LLVM pass to canonicalize addrspaces                        |
| `llvm-ptls.cpp`                  | Custom LLVM pass to lower TLS operations                           |
| `llvm-remove-addrspaces.cpp`     | Custom LLVM pass to remove Julia addrspaces                        |
| `llvm-remove-ni.cpp`             | Custom LLVM pass to remove Julia non-integral addrspaces           |
| `llvm-simdloop.cpp`              | Custom LLVM pass for [`@simd`](@ref)                               |
| `pipeline.cpp`                   | New pass manager pipeline, pass pipeline parsing                   |
| `sys.c`                          | I/O and operating system utility functions                         |

Einige der `.cpp`-Dateien bilden eine Gruppe, die zu einem einzelnen Objekt kompiliert.

Der Unterschied zwischen einem Intrinsic und einem Builtin besteht darin, dass ein Builtin eine First-Class-Funktion ist, die wie jede andere Julia-Funktion verwendet werden kann. Ein Intrinsic kann nur auf unboxed Daten operieren, und daher müssen seine Argumente statisch typisiert sein.

### [Alias Analysis](@id LLVM-Alias-Analysis)

Julia verwendet derzeit LLVM's [Type Based Alias Analysis](https://llvm.org/docs/LangRef.html#tbaa-metadata). Um die Kommentare zu finden, die die Einschlussbeziehungen dokumentieren, suchen Sie nach `static MDNode*` in `src/codegen.cpp`.

Die `-O` Option aktiviert LLVMs [Basic Alias Analysis](https://llvm.org/docs/AliasAnalysis.html#the-basic-aa-pass).

## Building Julia with a different version of LLVM

Die Standardversion von LLVM ist in `deps/llvm.version` angegeben. Sie können sie überschreiben, indem Sie eine Datei namens `Make.user` im Hauptverzeichnis erstellen und eine Zeile wie folgt hinzufügen:

```
LLVM_VER = 13.0.0
```

Neben den LLVM-Versionen können Sie auch `DEPS_GIT = llvm` in Kombination mit `USE_BINARYBUILDER_LLVM = 0` verwenden, um gegen die neueste Entwicklungsversion von LLVM zu bauen.

Sie können auch angeben, dass eine Debug-Version von LLVM erstellt werden soll, indem Sie entweder `LLVM_DEBUG = 1` oder `LLVM_DEBUG = Release` in Ihrer `Make.user`-Datei festlegen. Erstere wird ein vollständig unoptimiertes Build von LLVM sein, während letztere ein optimiertes Build von LLVM erzeugt. Je nach Ihren Bedürfnissen reicht letzteres aus und ist deutlich schneller. Wenn Sie `LLVM_DEBUG = Release` verwenden, sollten Sie auch `LLVM_ASSERTIONS = 1` festlegen, um Diagnosen für verschiedene Pässe zu aktivieren. Nur `LLVM_DEBUG = 1` impliziert diese Option standardmäßig.

## Passing options to LLVM

Sie können Optionen an LLVM über die Umgebungsvariable [`JULIA_LLVM_ARGS`](@ref JULIA_LLVM_ARGS) übergeben. Hier sind Beispielkonfigurationen mit `bash`-Syntax:

  * `export JULIA_LLVM_ARGS=-print-after-all` gibt IR nach jedem Durchgang aus.
  * `export JULIA_LLVM_ARGS=-debug-only=loop-vectorize` gibt LLVM `DEBUG(...)` Diagnosen für den Schleifenvektorizer aus. Wenn Sie Warnungen über "Unbekanntes Befehlszeilenargument" erhalten, bauen Sie LLVM mit `LLVM_ASSERTIONS = 1` neu.
  * `export JULIA_LLVM_ARGS=-help` zeigt eine Liste der verfügbaren Optionen. `export JULIA_LLVM_ARGS=-help-hidden` zeigt noch mehr.
  * `export JULIA_LLVM_ARGS="-fatal-warnings -print-options"` ist ein Beispiel, wie man mehrere Optionen verwendet.

### Useful `JULIA_LLVM_ARGS` parameters

  * `-print-after=PASS`: druckt die IR nach jeder Ausführung von `PASS`, nützlich zum Überprüfen von Änderungen, die durch einen Pass vorgenommen wurden.
  * `-print-before=PASS`: druckt die IR vor der Ausführung von `PASS`, nützlich zur Überprüfung der Eingabe für einen Pass.
  * `-print-changed`: Gibt die IR aus, wann immer ein Pass die IR ändert, nützlich, um einzugrenzen, welche Pässe Probleme verursachen.
  * `-print-(before|after)=MARKER-PASS`: Die Julia-Pipeline wird mit einer Reihe von Marker-Pässen geliefert, die in der Pipeline verwendet werden können, um zu identifizieren, wo Probleme oder Optimierungen auftreten. Ein Marker-Pass wird definiert als ein Pass, der einmal in der Pipeline erscheint und keine Transformationen am IR vornimmt und nur nützlich ist, um print-before/print-after anzusprechen. Derzeit existieren die folgenden Marker-Pässe in der Pipeline:

      * VorOptimierung
      * VorFrüheVereinfachung
      * NachFrüherVereinfachung
      * VorzeitigeOptimierung
      * NachFrüherOptimierung
      * VorSchleifenOptimierung
      * VorLICM
      * NachLICM
      * VorSchleifenVereinfachung
      * NachSchleifenVereinfachung
      * NachSchleifenOptimierung
      * VorScalarOptimierung
      * NachSkalarOptimierung
      * VorDerVektorisierung
      * NachVektorisierung
      * VorintrinsischeAbsenkung
      * NachIntrinsicLowering
      * VorDerReinigung
      * NachBereinigung
      * NachOptimierung
  * `-time-passes`: gibt die für jeden Durchgang benötigte Zeit aus, nützlich, um zu identifizieren, welche Durchgänge lange dauern.
  * `-print-module-scope`: wird in Verbindung mit `-print-(before|after)` verwendet, um das gesamte Modul anstelle der vom Pass empfangenen IR-Einheit zu erhalten.
  * `-debug`: gibt eine Menge Debugging-Informationen in LLVM aus
  * `-debug-only=NAME`, gibt Debugging-Anweisungen aus Dateien aus, bei denen `DEBUG_TYPE` auf `NAME` definiert ist, nützlich, um zusätzlichen Kontext zu einem Problem zu erhalten.

## Debugging LLVM transformations in isolation

Gelegentlich kann es nützlich sein, die Transformationen von LLVM isoliert vom Rest des Julia-Systems zu debuggen, z. B. weil die Reproduktion des Problems innerhalb von `julia` zu lange dauern würde oder weil man die Werkzeuge von LLVM (z. B. bugpoint) nutzen möchte.

Um zu beginnen, können Sie die Entwicklertools installieren, um mit LLVM zu arbeiten, indem Sie:

```
make -C deps install-llvm-tools
```

Um unoptimierten IR für das gesamte System-Image zu erhalten, übergeben Sie die Option `--output-unopt-bc unopt.bc` an den Build-Prozess des System-Images, der den unoptimierten IR in eine Datei `unopt.bc` ausgibt. Diese Datei kann dann wie gewohnt an LLVM-Tools übergeben werden. `libjulia` kann als LLVM-Pass-Plugin fungieren und in LLVM-Tools geladen werden, um julia-spezifische Pässe in dieser Umgebung verfügbar zu machen. Darüber hinaus bietet es den `-julia` Meta-Pass, der die gesamte Julia-Pass-Pipeline über den IR ausführt. Als Beispiel, um ein System-Image mit dem alten Pass-Manager zu generieren, könnte man Folgendes tun:

```

llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

Um ein Systemabbild mit dem neuen Passwortmanager zu erstellen, könnte man Folgendes tun:

```
opt -load-pass-plugin=libjulia-codegen.so --passes='julia' -o opt.bc unopt.bc
llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

Dieses Systemabbild kann dann wie gewohnt von `julia` geladen werden.

Es ist auch möglich, ein LLVM IR-Modul nur für eine Julia-Funktion zu dumpen, indem man:

```julia
fun, T = +, Tuple{Int,Int} # Substitute your function of interest here
optimize = false
open("plus.ll", "w") do file
    println(file, InteractiveUtils._dump_function(fun, T, false, false, false, true, :att, optimize, :default, false))
end
```

Diese Dateien können auf die gleiche Weise wie das oben gezeigte unoptimierte sysimg IR verarbeitet werden.

## Running the LLVM test suite

Um die LLVM-Tests lokal auszuführen, müssen Sie zuerst die Tools installieren, Julia bauen und dann können Sie die Tests ausführen:

```
make -C deps install-llvm-tools
make -j julia-src-release
make -C test/llvmpasses
```

Wenn Sie die einzelnen Testdateien direkt über die Befehle am Anfang jeder Testdatei ausführen möchten, wird der erste Schritt hier die Werkzeuge in `./usr/tools/opt` installiert haben. Dann möchten Sie manuell `%s` durch den Namen der Testdatei ersetzen.

## Improving LLVM optimizations for Julia

Die Verbesserung der LLVM-Codegenerierung beinhaltet normalerweise entweder die Anpassung der Julia-Transformation, um LLVMs Pässe besser zu unterstützen, oder die Verbesserung eines Pässe.

Wenn Sie planen, einen Pass zu verbessern, sollten Sie sicherstellen, dass Sie die [LLVM developer policy](https://llvm.org/docs/DeveloperPolicy.html) lesen. Die beste Strategie besteht darin, ein Codebeispiel in einer Form zu erstellen, in der Sie das `opt`-Tool von LLVM verwenden können, um es und den interessierenden Pass isoliert zu studieren.

1. Create an example Julia code of interest.
2. Verwenden Sie `JULIA_LLVM_ARGS=-print-after-all`, um das IR auszugeben.
3. Wählen Sie das IR an dem Punkt aus, kurz bevor der interessierende Pass ausgeführt wird.
4. Entfernen Sie die Debug-Metadaten und korrigieren Sie die TBAA-Metadaten von Hand.

Der letzte Schritt ist arbeitsintensiv. Vorschläge für eine bessere Vorgehensweise wären willkommen.

## The jlcall calling convention

Julia hat ein generisches Aufrufkonvention für nicht optimierten Code, die ungefähr wie folgt aussieht:

```c
jl_value_t *any_unoptimized_call(jl_value_t *, jl_value_t **, int);
```

wo die erste Argument das verpackte Funktionsobjekt ist, das zweite Argument ein Array von Argumenten auf dem Stack ist und das dritte die Anzahl der Argumente ist. Nun könnten wir eine einfache Senkung durchführen und eine Allokation für das Argument-Array ausgeben. Dies würde jedoch die SSA-Natur der Verwendungen am Aufrufort verraten, was Optimierungen (einschließlich der Platzierung von GC-Wurzeln) erheblich erschweren würde. Stattdessen geben wir es wie folgt aus:

```llvm
call %jl_value_t *@julia.call(jl_value_t *(*)(...) @any_unoptimized_call, %jl_value_t *%arg1, %jl_value_t *%arg2)
```

Dies ermöglicht es uns, die SSA-Eigenschaft der Verwendungen im gesamten Optimierer beizubehalten. Die Platzierung der GC-Wurzel wird diesen Aufruf später auf das ursprüngliche C-ABI herabsetzen.

## GC root placement

Die Platzierung von GC-Wurzeln erfolgt durch einen LLVM-Pass spät in der Pass-Pipeline. Die Durchführung der GC-Wurzelplatzierung zu diesem späten Zeitpunkt ermöglicht es LLVM, aggressivere Optimierungen rund um Code vorzunehmen, der GC-Wurzeln erfordert, und ermöglicht es uns, die Anzahl der erforderlichen GC-Wurzeln und GC-Wurzel-Speicheroperationen zu reduzieren (da LLVM unser GC nicht versteht, wüsste es sonst nicht, was es mit Werten, die im GC-Rahmen gespeichert sind, tun darf und was nicht, daher wird es konservativ sehr wenig tun). Als Beispiel betrachten Sie einen Fehlerpfad.

```julia
if some_condition()
    #= Use some variables maybe =#
    error("An error occurred")
end
```

Während der konstanten Faltung kann LLVM feststellen, dass die Bedingung immer falsch ist, und den Basisblock entfernen. Wenn jedoch das GC-Root-Senken frühzeitig durchgeführt wird, würden die GC-Root-Slots, die im gelöschten Block verwendet werden, sowie alle Werte, die nur aufgrund ihrer Verwendung im Fehlerpfad am Leben gehalten werden, von LLVM am Leben gehalten. Indem wir das GC-Root-Senken spät durchführen, geben wir LLVM die Erlaubnis, alle seine üblichen Optimierungen (konstante Faltung, Eliminierung toter Codes usw.) durchzuführen, ohne sich (zu sehr) darum kümmern zu müssen, welche Werte möglicherweise oder möglicherweise nicht vom GC verfolgt werden.

Um jedoch in der Lage zu sein, eine späte GC-Root-Platzierung durchzuführen, müssen wir in der Lage sein, a) welche Zeiger GC-überwacht sind und b) alle Verwendungen solcher Zeiger zu identifizieren. Das Ziel des GC-Platzierungspasses ist somit einfach:

Minimieren Sie die Anzahl der benötigten GC-Wurzeln/Speicherplätze für sie, unter der Bedingung, dass zu jedem Safepoint jeder lebende, von der GC verfolgte Zeiger (d.h. für den es nach diesem Punkt einen Pfad gibt, der eine Verwendung dieses Zeigers enthält) in einem GC-Slot ist.

### Representation

Die primäre Schwierigkeit besteht darin, eine IR-Darstellung auszuwählen, die es uns ermöglicht, GC-verfolgte Zeiger und deren Verwendung zu identifizieren, selbst nachdem das Programm durch den Optimierer gelaufen ist. Unser Design nutzt drei LLVM-Funktionen, um dies zu erreichen:

  * Benutzerdefinierte Adressräume
  * Operand-Bündel
  * Nicht-integrale Zeiger

Benutzerdefinierte Adressräume ermöglichen es uns, jeden Punkt mit einer Ganzzahl zu kennzeichnen, die durch Optimierungen erhalten bleiben muss. Der Compiler darf keine Umwandlungen zwischen Adressräumen einfügen, die im ursprünglichen Programm nicht vorhanden waren, und er darf niemals den Adressraum eines Zeigers bei einer Lade-/Speicher-/usw. Operation ändern. Dies ermöglicht es uns, zu kennzeichnen, welche Zeiger GC-verfolgt werden, auf eine optimierungsresistente Weise. Beachten Sie, dass Metadaten nicht dasselbe Ziel erreichen könnten. Metadaten sollen immer verworfen werden können, ohne die Semantik des Programms zu verändern. Das Versäumnis, einen GC-verfolgten Zeiger zu identifizieren, verändert jedoch das Verhalten des resultierenden Programms dramatisch - es wird wahrscheinlich abstürzen oder falsche Ergebnisse zurückgeben. Derzeit verwenden wir drei verschiedene Adressräume (ihre Nummern sind in `src/codegen_shared.cpp` definiert):

  * GC Verfolgte Zeiger (derzeit 10): Dies sind Zeiger auf verpackte Werte, die in einen GC-Rahmen eingefügt werden können. Es ist grob äquivalent zu einem `jl_value_t*` Zeiger auf der C-Seite. Hinweis: Es ist illegal, jemals einen Zeiger in diesem Adressraum zu haben, der möglicherweise nicht in einem GC-Slot gespeichert werden kann.
  * Abgeleitete Zeiger (derzeit 11): Dies sind Zeiger, die aus einem von der GC verfolgten Zeiger abgeleitet sind. Verwendungen dieser Zeiger erzeugen Verwendungen des ursprünglichen Zeigers. Sie müssen jedoch selbst nicht dem GC bekannt sein. Der GC-Wurzelplatzierungspass MUSS immer den von diesem Zeiger abgeleiteten, von der GC verfolgten Zeiger finden und diesen als Zeiger zur Wurzel verwenden.
  * Callee Rooted Pointers (derzeit 12): Dies ist ein Hilfsadressraum, um das Konzept eines callee-gegründeten Wertes auszudrücken. Alle Werte dieses Adressraums MÜSSEN in einem GC-Wurzel gespeichert werden (obwohl es möglich ist, diese Bedingung in Zukunft zu lockern), müssen jedoch im Gegensatz zu den anderen Zeigern nicht verankert sein, wenn sie an einen Aufruf übergeben werden (sie müssen jedoch verankert sein, wenn sie zwischen der Definition und dem Aufruf über einen anderen Safepoint hinweg aktiv sind).
  * Zeiger, die von verfolgten Objekten geladen wurden (derzeit 13): Dies wird von Arrays verwendet, die selbst einen Zeiger auf die verwalteten Daten enthalten. Dieser Datenbereich gehört dem Array, ist jedoch selbst kein von der GC verfolgtes Objekt. Der Compiler garantiert, dass solange dieser Zeiger aktiv ist, das Objekt, von dem dieser Zeiger geladen wurde, weiterhin aktiv bleibt.

### Invariants

Der GC-Root-Platzierungspass nutzt mehrere Invarianten, die vom Frontend beachtet werden müssen und die vom Optimierer erhalten bleiben.

Zuerst sind nur die folgenden Adressraum-Casts erlaubt:

  * 0->{Verfolgt,Abgeleitet,CalleeRooted}: Es ist zulässig, einen nicht verfolgten Zeiger in jeden der anderen zu dekadieren. Beachten Sie jedoch, dass der Optimierer weitreichende Befugnisse hat, um einen solchen Wert nicht zu verankern. Es ist niemals sicher, einen Wert im Adressraum 0 in irgendeinem Teil des Programms zu haben, wenn er (oder von ihm abgeleitet ist) ein Wert ist, der eine GC-Wurzel erfordert.
  * Verfolgt->Abgeleitet: Dies ist der Standardzerfallsweg für Innenwerte. Der Platzierungsdurchlauf wird nach diesen suchen, um den Basiszeiger für jede Verwendung zu identifizieren.
  * Verfolgt->CalleeRooted: Der Adressraum CalleeRooted dient lediglich als Hinweis, dass eine GC-Wurzel nicht erforderlich ist. Beachten Sie jedoch, dass der Derived->CalleeRooted-Verfall verboten ist, da Zeiger im Allgemeinen in einem GC-Slot gespeichert werden sollten, selbst in diesem Adressraum.

Jetzt lassen Sie uns betrachten, was einen Gebrauch ausmacht:

  * Ladungen, deren geladene Werte sich in einem der Adressräume befinden
  * Speichert einen Wert in einem der Adressräume an einem Ort.
  * Speichert einen Zeiger in einem der Adressräume
  * Aufrufe, bei denen ein Wert in einem der Adressräume ein Operand ist
  * Aufrufe im jlcall ABI, für die das Argumentarray einen Wert enthält
  * Bitte fügen Sie den Markdown-Inhalt oder den Text ein, den Sie übersetzen möchten.

Wir erlauben ausdrücklich Lade-/Speicheroperationen und einfache Aufrufe in den Adressräumen Tracked/Derived. Elemente von jlcall-Argumentarrays müssen sich immer im Adressraum Tracked befinden (es ist durch die ABI erforderlich, dass sie gültige `jl_value_t*`-Zeiger sind). Das Gleiche gilt für Rückgabeanweisungen (obwohl zu beachten ist, dass Struktur-Rückgabeargumente in jedem der Adressräume erlaubt sind). Die einzige zulässige Verwendung eines CalleeRooted-Zeigers im Adressraum besteht darin, ihn an einen Aufruf zu übergeben (der einen entsprechend typisierten Operanden haben muss).

Darüber hinaus verbieten wir `getelementptr` im Adressraum Tracked. Dies liegt daran, dass der resultierende Zeiger, es sei denn, die Operation ist ein Noop, nicht gültig in einem GC-Slot gespeichert werden kann und daher möglicherweise nicht in diesem Adressraum vorhanden ist. Wenn ein solcher Zeiger erforderlich ist, sollte er zuerst in den Adressraum Derived umgewandelt werden.

Zuletzt verbieten wir `inttoptr`/`ptrtoint`-Anweisungen in diesen Adressräumen. Das Vorhandensein dieser Anweisungen würde bedeuten, dass einige `i64`-Werte tatsächlich von der GC verfolgt werden. Das ist problematisch, da es die festgelegte Anforderung verletzt, dass wir GC-relevante Zeiger identifizieren können. Diese Invarianz wird mit der LLVM-Funktion "nicht-integrale Zeiger" erreicht, die neu in LLVM 5.0 ist. Sie verbietet dem Optimierer, Optimierungen vorzunehmen, die diese Operationen einführen würden. Beachten Sie, dass wir zur JIT-Zeit weiterhin statische Konstanten einfügen können, indem wir `inttoptr` im Adressraum 0 verwenden und dann anschließend in den entsprechenden Adressraum übergehen.

### Supporting [`ccall`](@ref)

Ein wichtiger Aspekt, der in der bisherigen Diskussion fehlt, ist der Umgang mit [`ccall`](@ref). `4d61726b646f776e2e436f64652822222c20226363616c6c2229_40726566` hat das besondere Merkmal, dass der Standort und der Geltungsbereich einer Verwendung nicht übereinstimmen. Als Beispiel betrachten Sie:

```julia
A = randn(1024)
ccall(:foo, Cvoid, (Ptr{Float64},), A)
```

Beim Senken wird der Compiler eine Umwandlung vom Array zum Zeiger einfügen, die die Referenz auf den Array-Wert entfernt. Wir müssen jedoch sicherstellen, dass das Array während der Ausführung von [`ccall`](@ref) am Leben bleibt. Um zu verstehen, wie dies geschieht, betrachten wir eine hypothetische, ungefähre mögliche Senkung des obigen Codes:

```julia
return $(Expr(:foreigncall, :(:foo), Cvoid, svec(Ptr{Float64}), 0, :(:ccall), Expr(:foreigncall, :(:jl_array_ptr), Ptr{Float64}, svec(Any), 0, :(:ccall), :(A)), :(A)))
```

Der letzte `:(A)`, ist eine zusätzliche Argumentliste, die während der Senkung eingefügt wird und den Codegenerator darüber informiert, welche Julia-Level-Werte für die Dauer dieses [`ccall`](@ref) am Leben gehalten werden müssen. Wir nehmen dann diese Informationen und stellen sie auf der IR-Ebene in einem "Operand-Bundle" dar. Ein Operand-Bundle ist im Wesentlichen eine gefälschte Verwendung, die an der Aufrufstelle angehängt wird. Auf der IR-Ebene sieht das so aus:

```llvm
call void inttoptr (i64 ... to void (double*)*)(double* %5) [ "jl_roots"(%jl_value_t addrspace(10)* %A) ]
```

Der GC-Root-Platzierungspass behandelt das `jl_roots` Operandenbündel, als ob es ein regulärer Operand wäre. Als letzter Schritt, nachdem die GC-Roots eingefügt wurden, wird das Operandenbündel entfernt, um Verwirrung bei der Instruktionsauswahl zu vermeiden.

### Supporting [`pointer_from_objref`](@ref)

[`pointer_from_objref`](@ref) ist besonders, weil es vom Benutzer erfordert, die Kontrolle über das GC-Routing explizit zu übernehmen. Nach unseren oben genannten Invarianten ist diese Funktion illegal, da sie einen Adressraum-Cast von 10 auf 0 durchführt. Sie kann jedoch in bestimmten Situationen nützlich sein, daher bieten wir ein spezielles intrinsisches an:

```llvm
declared %jl_value_t *julia.pointer_from_objref(%jl_value_t addrspace(10)*)
```

welches auf den entsprechenden Adressraum nach der Senkung des GC-Wurzeltyps umgewandelt wird. Beachten Sie jedoch, dass der Aufrufer durch die Verwendung dieses Intrinsics die volle Verantwortung dafür übernimmt, dass der betreffende Wert verwurzelt ist. Darüber hinaus wird dieser Intrinsic nicht als Verwendung betrachtet, sodass der GC-Wurzelplatzierungsdurchlauf keinen GC-Wurzel für die Funktion bereitstellt. Infolgedessen muss das externe Wurzeln arrangiert werden, während der Wert noch vom System verfolgt wird. D.h. es ist nicht gültig, zu versuchen, das Ergebnis dieser Operation zu verwenden, um eine globale Wurzel zu etablieren - der Optimierer hat den Wert möglicherweise bereits verworfen.

### Keeping values alive in the absence of uses

In bestimmten Fällen ist es notwendig, ein Objekt am Leben zu halten, auch wenn es keine vom Compiler sichtbare Verwendung dieses Objekts gibt. Dies kann der Fall sein für Low-Level-Code, der direkt auf die Speicherrepräsentation eines Objekts zugreift, oder für Code, der mit C-Code interagieren muss. Um dies zu ermöglichen, bieten wir die folgenden Intrinsics auf LLVM-Ebene an:

```
token @llvm.julia.gc_preserve_begin(...)
void @llvm.julia.gc_preserve_end(token)
```

(Das `llvm.` im Namen ist erforderlich, um den `token`-Typ verwenden zu können). Die Semantik dieser Intrinsics ist wie folgt: An jedem Safepoint, der von einem `gc_preserve_begin`-Aufruf dominiert wird, aber nicht von einem entsprechenden `gc_preserve_end`-Aufruf dominiert wird (d.h. einem Aufruf, dessen Argument der Token ist, der von einem `gc_preserve_begin`-Aufruf zurückgegeben wird), werden die als Argumente an den `gc_preserve_begin` übergebenen Werte lebendig gehalten. Beachten Sie, dass der `gc_preserve_begin` weiterhin als reguläre Verwendung dieser Werte zählt, sodass die standardmäßigen Lebensdauersemantiken sicherstellen, dass die Werte vor dem Betreten des Erhaltungsbereichs lebendig gehalten werden.
