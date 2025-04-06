# Eval of Julia code

Einer der schwierigsten Teile beim Lernen, wie die Julia-Sprache Code ausführt, ist das Verständnis, wie all die Teile zusammenarbeiten, um einen Codeblock auszuführen.

Jeder Codeabschnitt durchläuft typischerweise viele Schritte mit potenziell unbekannten Namen, wie (in keiner bestimmten Reihenfolge): flisp, AST, C++, LLVM, `eval`, `typeinf`, `macroexpand`, sysimg (oder Systembild), Bootstrapping, kompilieren, parsen, ausführen, JIT, interpretieren, boxen, unboxen, intrinsische Funktion und primitive Funktion, bevor er in das gewünschte Ergebnis (hoffentlich) umgewandelt wird.

!!! sidebar "Definitions"
      * REPL

        REPL steht für Read-Eval-Print Loop. So nennen wir einfach die Befehlszeilenumgebung kurz.
      * AST

        Abstract Syntax Tree Der AST ist die digitale Darstellung der Code-Struktur. In dieser Form wurde der Code für die Bedeutung tokenisiert, sodass er besser für die Manipulation und Ausführung geeignet ist.


![Diagramm des Compiler-Flusses](./img/compiler_diagram.png)

## Julia Execution

Die 10.000-Fuß-Perspektive des gesamten Prozesses ist wie folgt:

1. Der Benutzer startet `julia`.
2. Die C-Funktion `main()` aus `cli/loader_exe.c` wird aufgerufen. Diese Funktion verarbeitet die Befehlszeilenargumente, füllt die Struktur `jl_options` aus und setzt die Variable `ARGS`. Anschließend initialisiert sie Julia (indem sie [`julia_init` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) aufruft, was möglicherweise ein zuvor kompiliertes [sysimg](@ref dev-sysimg) lädt. Schließlich übergibt sie die Kontrolle an Julia, indem sie [`Base._start()`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) aufruft.
3. Wenn `_start()` die Kontrolle übernimmt, hängt die nachfolgende Befehlsfolge von den übergebenen Befehlszeilenargumenten ab. Wenn beispielsweise ein Dateiname angegeben wurde, wird es fortfahren, diese Datei auszuführen. Andernfalls wird es eine interaktive REPL starten.
4. Die Details darüber, wie der REPL mit dem Benutzer interagiert, lassen wir weg. Sagen wir einfach, dass das Programm am Ende mit einem Block von Code endet, den es ausführen möchte.
5. Wenn der Codeblock, der ausgeführt werden soll, in einer Datei ist, wird [`jl_load(char *filename)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) aufgerufen, um die Datei zu laden, und [parse](@ref dev-parsing) wird ausgeführt. Jedes Fragment des Codes wird dann an `eval` übergeben, um es auszuführen.
6. Jedes Codefragment (oder AST) wird an [`eval()`](@ref) übergeben, um Ergebnisse zu erzeugen.
7. [`eval()`](@ref) führt jedes Codefragment aus und versucht, es in [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) auszuführen.
8. `jl_toplevel_eval_flex()` entscheidet, ob der Code eine "Toplevel"-Aktion (wie `using` oder `module`) ist, die innerhalb einer Funktion ungültig wäre. Falls ja, übergibt es den Code an den Toplevel-Interpreter.
9. `jl_toplevel_eval_flex()` dann [expands](@ref dev-macro-expansion) der Code, um alle Makros zu eliminieren und den AST zu "vereinfachen", um ihn einfacher auszuführen.
10. `jl_toplevel_eval_flex()` verwendet dann einige einfache Heuristiken, um zu entscheiden, ob der AST JIT-compiliert oder direkt interpretiert werden soll.
11. Der Großteil der Arbeit zur Interpretation von Code wird von [`eval` in `interpreter.c`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c) behandelt.
12. Wenn stattdessen der Code kompiliert wird, wird der Großteil der Arbeit von `codegen.cpp` erledigt. Jedes Mal, wenn eine Julia-Funktion zum ersten Mal mit einem bestimmten Satz von Argumenttypen aufgerufen wird, wird [type inference](@ref dev-type-inference) für diese Funktion ausgeführt. Diese Informationen werden vom Schritt [codegen](@ref dev-codegen) verwendet, um schnelleren Code zu generieren.
13. Schließlich verlässt der Benutzer die REPL oder das Ende des Programms wird erreicht, und die Methode `_start()` gibt zurück.
14. Kurz vor dem Verlassen ruft `main()` [`jl_atexit_hook(exit_code)`](https://github.com/JuliaLang/julia/blob/master/src/init.c) auf. Dies ruft `Base._atexit()` auf (das alle Funktionen aufruft, die in [`atexit()`](@ref) innerhalb von Julia registriert sind). Dann ruft es [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) auf. Schließlich räumt es alle `libuv`-Handles ordentlich auf und wartet, bis sie geleert und geschlossen sind.

## [Parsing](@id dev-parsing)

Der Julia-Parser ist ein kleines Lisp-Programm, das in Femtolisp geschrieben ist. Der Quellcode dafür ist in Julia unter [src/flisp](https://github.com/JuliaLang/julia/tree/master/src/flisp) verteilt.

Die Schnittstellenfunktionen dafür sind hauptsächlich in [`jlfrontend.scm`](https://github.com/JuliaLang/julia/blob/master/src/jlfrontend.scm) definiert. Der Code in [`ast.c`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) behandelt diesen Übergang auf der Julia-Seite.

Die anderen relevanten Dateien in diesem Stadium sind [`julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm), die das Tokenisieren von Julia-Code und die Umwandlung in einen AST behandelt, und [`julia-syntax.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-syntax.scm), die die Umwandlung komplexer AST-Darstellungen in einfachere, "niedrigere" AST-Darstellungen behandelt, die besser für die Analyse und Ausführung geeignet sind.

Wenn Sie den Parser testen möchten, ohne Julia vollständig neu zu erstellen, können Sie das Frontend wie folgt eigenständig ausführen:

```
$ cd src
$ flisp/flisp
> (load "jlfrontend.scm")
> (jl-parse-file "<filename>")
```

## [Macro Expansion](@id dev-macro-expansion)

Wenn [`eval()`](@ref) auf ein Makro trifft, erweitert es diesen AST-Knoten, bevor es versucht, den Ausdruck auszuwerten. Die Makroerweiterung umfasst einen Übergang von `4d61726b646f776e2e436f64652822222c20226576616c28292229_40726566` (in Julia) zur Parserfunktion `jl_macroexpand()` (geschrieben in `flisp`) zum Julia-Makro selbst (geschrieben in - was sonst - Julia) über `fl_invoke_julia_macro()` und zurück.

Typischerweise wird die Makroerweiterung als erster Schritt während eines Aufrufs von [`Meta.lower()`](@ref)/`jl_expand()` aufgerufen, obwohl sie auch direkt durch einen Aufruf von [`macroexpand()`](@ref)/`jl_macroexpand()` aufgerufen werden kann.

## [Type Inference](@id dev-type-inference)

Typinferenz wird in Julia durch [`typeinf()` in `compiler/typeinfer.jl`](https://github.com/JuliaLang/julia/blob/master/base/compiler/typeinfer.jl) implementiert. Typinferenz ist der Prozess, bei dem eine Julia-Funktion untersucht wird, um Grenzen für die Typen ihrer Variablen sowie Grenzen für den Typ des Rückgabewerts der Funktion zu bestimmen. Dies ermöglicht viele zukünftige Optimierungen, wie das Unboxing bekannter unveränderlicher Werte und das Hoisting von verschiedenen Laufzeitoperationen zur Compile-Zeit, wie das Berechnen von Feldoffsets und Funktionszeigern. Die Typinferenz kann auch andere Schritte wie die Konstantenweitergabe und Inlining umfassen.

!!! sidebar "More Definitions"
      * JIT

        Just-In-Time-Kompilierung Der Prozess, native Maschinenanweisungen in den Speicher zu generieren, genau dann, wenn sie benötigt werden.
      * LLVM

        Low-Level Virtual Machine (ein Compiler) Der Julia JIT-Compiler ist ein Programm/Bibliothek namens libLLVM. Die Codegenerierung in Julia bezieht sich sowohl auf den Prozess, einen Julia AST zu nehmen und ihn in LLVM-Anweisungen umzuwandeln, als auch auf den Prozess, bei dem LLVM dies optimiert und in native Assembler-Anweisungen umwandelt.
      * C++

        Die Programmiersprache, in der LLVM implementiert ist, was bedeutet, dass auch die Codegenerierung in dieser Sprache implementiert ist. Der Rest von Julias Bibliothek ist in C implementiert, teilweise weil ihr kleinerer Funktionsumfang sie als Schnittstellenschicht zwischen verschiedenen Sprachen benutzbarer macht.
      * Kasten

        Dieser Begriff wird verwendet, um den Prozess zu beschreiben, bei dem ein Wert genommen und ein Wrapper um die Daten gelegt wird, die vom Garbage Collector (gc) verfolgt werden und mit dem Typ des Objekts gekennzeichnet sind.
      * unbox

        Die Umkehrung des Boxens eines Wertes. Diese Operation ermöglicht eine effizientere Manipulation von Daten, wenn der Typ dieser Daten zur Compile-Zeit vollständig bekannt ist (durch Typinferenz).
      * generische Funktion

        Eine Julia-Funktion, die aus mehreren "Methoden" besteht, die basierend auf der Argumenttyp-Signatur für die dynamische Dispatch ausgewählt werden.
      * anonyme Funktion oder "Methode"

        Eine Julia-Funktion ohne Namen und ohne Typ-Dispatch-Fähigkeiten
      * primitive Funktion

        Eine in C implementierte Funktion, die in Julia als benannte Funktion "Methode" exponiert wird (wenn auch ohne die Fähigkeiten zur generischen Funktionsdispatch, ähnlich einer anonymen Funktion).
      * intrinsische Funktion

        Eine Low-Level-Operation, die als Funktion in Julia exponiert ist. Diese Pseudo-Funktionen implementieren Operationen auf Rohbits wie Addition und Vorzeichenverlängerung, die auf keine andere Weise direkt ausgedrückt werden können. Da sie direkt auf Bits arbeiten, müssen sie in eine Funktion kompiliert und von einem Aufruf zu `Core.Intrinsics.box(T, ...)` umgeben werden, um die Typinformationen dem Wert neu zuzuweisen.


## [JIT Code Generation](@id dev-codegen)

Codegen ist der Prozess, bei dem einen Julia AST in nativen Maschinencode umgewandelt wird.

Die JIT-Umgebung wird durch einen frühen Aufruf von [`jl_init_codegen` in `codegen.cpp`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp) initialisiert.

Auf Anfrage wird eine Julia-Methode durch die Funktion `emit_function(jl_method_instance_t*)` in eine native Funktion umgewandelt. (Hinweis: Bei der Verwendung des MCJIT (in LLVM v3.4+) muss jede Funktion in ein neues Modul JIT-kompiliert werden.) Diese Funktion ruft rekursiv `emit_expr()` auf, bis die gesamte Funktion ausgegeben wurde.

Ein Großteil des verbleibenden Inhalts dieser Datei ist verschiedenen manuellen Optimierungen spezifischer Code-Muster gewidmet. Zum Beispiel weiß `emit_known_call()`, wie man viele der primitiven Funktionen (definiert in [`builtins.c`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c)) für verschiedene Kombinationen von Argumenttypen inline einfügen kann.

Andere Teile von Codegen werden von verschiedenen Hilfsdateien behandelt:

  * [`debuginfo.cpp`](https://github.com/JuliaLang/julia/blob/master/src/debuginfo.cpp)

    Behandelt Backtraces für JIT-Funktionen
  * [`ccall.cpp`](https://github.com/JuliaLang/julia/blob/master/src/ccall.cpp)

    Behandelt die ccall- und llvmcall-FFI sowie verschiedene `abi_*.cpp`-Dateien.
  * [`intrinsics.cpp`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp)

    Behandelt die Emission verschiedener niederstufiger intrinsischer Funktionen

!!! sidebar "Bootstrapping"
    Der Prozess der Erstellung eines neuen Systemabbilds wird "Bootstrapping" genannt.

    Die Etymologie dieses Wortes stammt von dem Ausdruck "sich selbst an den Bootstraps hochziehen" und bezieht sich auf die Idee, von einer sehr begrenzten Menge an verfügbaren Funktionen und Definitionen auszugehen und mit der Schaffung einer voll funktionsfähigen Umgebung zu enden.


## [System Image](@id dev-sysimg)

Das Systemabbild ist ein vorkompiliertes Archiv einer Reihe von Julia-Dateien. Die mit Julia verteilte `sys.ji`-Datei ist ein solches Systemabbild, das durch die Ausführung der Datei [`sysimg.jl`](https://github.com/JuliaLang/julia/blob/master/base/sysimg.jl) und die Serialisierung der resultierenden Umgebung (einschließlich Typen, Funktionen, Module und aller anderen definierten Werte) in eine Datei generiert wird. Daher enthält es eine eingefrorene Version der Module `Main`, `Core` und `Base` (und alles andere, was sich am Ende des Bootstrappings in der Umgebung befand). Dieser Serializer/Deserializer wird von [`jl_save_system_image`/`jl_restore_system_image` in `staticdata.c`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) implementiert.

Wenn keine sysimg-Datei vorhanden ist (`jl_options.image_file == NULL`), bedeutet dies auch, dass `--build` in der Befehlszeile angegeben wurde, sodass das endgültige Ergebnis eine neue sysimg-Datei sein sollte. Während der Julia-Initialisierung werden minimale `Core`- und `Main`-Module erstellt. Dann wird eine Datei namens `boot.jl` aus dem aktuellen Verzeichnis ausgewertet. Julia wertet dann jede Datei aus, die als Befehlszeilenargument angegeben ist, bis das Ende erreicht ist. Schließlich speichert es die resultierende Umgebung in einer "sysimg"-Datei, die als Ausgangspunkt für einen zukünftigen Julia-Durchlauf verwendet werden kann.
