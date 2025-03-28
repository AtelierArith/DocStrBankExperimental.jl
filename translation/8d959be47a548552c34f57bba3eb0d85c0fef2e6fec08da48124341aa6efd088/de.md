# [gdb debugging tips](@id gdb-debugging-tips)

## Displaying Julia variables

Innerhalb von `gdb` kann jedes `jl_value_t*`-Objekt `obj` angezeigt werden mit

```
(gdb) call jl_(obj)
```

Das Objekt wird in der `julia`-Sitzung angezeigt, nicht in der gdb-Sitzung. Dies ist eine nützliche Möglichkeit, die Typen und Werte von Objekten zu entdecken, die von Julias C-Code manipuliert werden.

Ähnlich, wenn Sie einige von Julias Interna (z. B. `compiler.jl`) debuggen, können Sie `obj` mit folgendem Befehl ausgeben:

```julia
ccall(:jl_, Cvoid, (Any,), obj)
```

Dies ist eine gute Möglichkeit, Probleme zu umgehen, die aus der Reihenfolge entstehen, in der Julias Ausgabeströme initialisiert werden.

Julias Flisp-Interpreter verwendet `value_t`-Objekte; diese können mit `call fl_print(fl_ctx, ios_stdout, obj)` angezeigt werden.

## Useful Julia variables for Inspecting

Während die Adressen vieler Variablen, wie Singletons, nützlich sein können, um viele Fehler zu drucken, gibt es eine Reihe zusätzlicher Variablen (siehe `julia.h` für eine vollständige Liste), die noch nützlicher sind.

  * (bei `jl_apply_generic`) `mfunc` und `jl_uncompress_ast(mfunc->def, mfunc->code)` :: um ein wenig über den Aufrufstapel herauszufinden
  * `jl_lineno` und `jl_filename` :: um herauszufinden, von welcher Zeile in einem Test man mit dem Debuggen beginnen soll (oder um herauszufinden, wie weit in eine Datei geparst wurde)
  * `$1` :: nicht wirklich eine Variable, aber dennoch eine nützliche Abkürzung, um auf das Ergebnis des letzten gdb-Befehls (wie `print`) zu verweisen.
  * `jl_options` :: manchmal nützlich, da es alle erfolgreich geparsten Befehlszeilenoptionen auflistet
  * `jl_uv_stderr` :: denn wer mag es nicht, mit stdio interagieren zu können

## Useful Julia functions for Inspecting those variables

  * `jl_print_task_backtraces(0)` :: Ähnlich wie gdbs `thread apply all bt` oder lldbs `thread backtrace all`. Führt alle Threads aus und druckt Backtraces für alle vorhandenen Aufgaben.
  * `jl_gdblookup($pc)` :: Zum Nachschlagen der aktuellen Funktion und Zeile.
  * `jl_gdblookupinfo($pc)` :: Zum Nachschlagen des aktuellen Methodeninstanzobjekts.
  * `jl_gdbdumpcode(mi)` :: Zum Dumpen aller `code_typed/code_llvm/code_asm`, wenn die REPL nicht richtig funktioniert.
  * `jlbacktrace()` :: Zum Dumpen des aktuellen Julia-Backtrace-Stacks nach stderr. Nur verwendbar, nachdem `record_backtrace()` aufgerufen wurde.
  * `jl_dump_llvm_value(Value*)` :: Zum Aufrufen von `Value->dump()` in gdb, wo es nicht nativ funktioniert. Zum Beispiel `f->linfo->functionObject`, `f->linfo->specFunctionObject` und `to_function(f->linfo)`.
  * `jl_dump_llvm_module(Module*)` :: Zum Aufrufen von `Module->dump()` in gdb, wo es nicht nativ funktioniert.
  * `Type->dump()` :: funktioniert nur in lldb. Hinweis: Fügen Sie etwas wie `;1` hinzu, um zu verhindern, dass lldb seinen Prompt über die Ausgabe druckt.
  * `jl_eval_string("expr")` :: zum Auslösen von Nebenwirkungen, um den aktuellen Zustand zu ändern oder um Symbole nachzuschlagen.
  * `jl_typeof(jl_value_t*)` :: zum Extrahieren des Typ-Tags eines Julia-Werts (in gdb, rufen Sie zuerst `macro define jl_typeof jl_typeof` auf, oder wählen Sie etwas Kurzes wie `ty` für das erste Argument, um eine Abkürzung zu definieren)

## Inserting breakpoints for inspection from gdb

In deiner `gdb`-Sitzung setze einen Haltepunkt in `jl_breakpoint` wie folgt:

```
(gdb) break jl_breakpoint
```

Dann fügen Sie in Ihren Julia-Code einen Aufruf zu `jl_breakpoint` hinzu, indem Sie

```julia
ccall(:jl_breakpoint, Cvoid, (Any,), obj)
```

wo `obj` kann jede Variable oder jedes Tupel sein, das Sie im Haltepunkt zugänglich machen möchten.

Es ist besonders hilfreich, zum `jl_apply`-Rahmen zurückzukehren, von dem aus Sie die Argumente einer Funktion anzeigen können, z. B.

```
(gdb) call jl_(args[0])
```

Ein weiteres nützliches Frame ist `to_function(jl_method_instance_t *li, bool cstyle)`. Das Argument `jl_method_instance_t*` ist eine Struktur mit einem Verweis auf den endgültigen AST, der an den Compiler gesendet wird. Zu diesem Zeitpunkt wird der AST jedoch normalerweise komprimiert sein; um den AST anzuzeigen, rufen Sie `jl_uncompress_ast` auf und übergeben Sie das Ergebnis an `jl_`:

```
#2  0x00007ffff7928bf7 in to_function (li=0x2812060, cstyle=false) at codegen.cpp:584
584          abort();
(gdb) p jl_(jl_uncompress_ast(li, li->ast))
```

## Inserting breakpoints upon certain conditions

### Loading a particular file

Angenommen, die Datei heißt `sysimg.jl`:

```
(gdb) break jl_load if strcmp(fname, "sysimg.jl")==0
```

### Calling a particular method

```
(gdb) break jl_apply_generic if strcmp((char*)(jl_symbol_name)(jl_gf_mtable(F)->name), "method_to_break")==0
```

Da diese Funktion für jeden Aufruf verwendet wird, machst du alles 1000x langsamer, wenn du das tust.

## Dealing with signals

Julia benötigt einige Signale, um ordnungsgemäß zu funktionieren. Der Profiler verwendet `SIGUSR2` für das Sampling und der Garbage Collector verwendet `SIGSEGV` zur Synchronisierung von Threads. Wenn Sie Code debuggen, der den Profiler oder mehrere Threads verwendet, möchten Sie möglicherweise, dass der Debugger diese Signale ignoriert, da sie während normaler Operationen sehr häufig ausgelöst werden können. Der Befehl, um dies in GDB zu tun, lautet (ersetzen Sie `SIGSEGV` durch `SIGUSR2` oder andere Signale, die Sie ignorieren möchten):

```
(gdb) handle SIGSEGV noprint nostop pass
```

Der entsprechende LLDB-Befehl ist (nachdem der Prozess gestartet wurde):

```
(lldb) pro hand -p true -s false -n false SIGSEGV
```

Wenn Sie einen Segfault mit mehrteiliger Code debuggen, können Sie einen Haltepunkt auf `jl_critical_error` setzen (auch `sigdie_handler` sollte unter Linux und BSD funktionieren), um nur den tatsächlichen Segfault zu erfassen und nicht die GC-Synchronisationspunkte.

## Debugging during Julia's build process (bootstrap)

Fehler, die während `make` auftreten, benötigen eine spezielle Behandlung. Julia wird in zwei Phasen gebaut, wobei `sys0` und `sys.ji` erstellt werden. Um zu sehen, welche Befehle zum Zeitpunkt des Fehlers ausgeführt werden, verwenden Sie `make VERBOSE=1`.

Zum Zeitpunkt dieses Schreibens können Sie Build-Fehler während der `sys0`-Phase aus dem `base`-Verzeichnis mit folgendem Befehl debuggen:

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys0 sysimg.jl
```

Sie müssen möglicherweise alle Dateien in `usr/lib/julia/` löschen, damit dies funktioniert.

Sie können die `sys.ji`-Phase debuggen, indem Sie:

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys -J ../usr/lib/julia/sys0.ji sysimg.jl
```

Standardmäßig führt jeder Fehler dazu, dass Julia beendet wird, selbst unter gdb. Um einen Fehler "in flagranti" zu erfassen, setzen Sie einen Haltepunkt in `jl_error` (es gibt mehrere andere nützliche Stellen für spezifische Arten von Fehlern, einschließlich: `jl_too_few_args`, `jl_too_many_args` und `jl_throw`).

Sobald ein Fehler erkannt wird, ist eine nützliche Technik, den Stack nach oben zu durchlaufen und die Funktion zu untersuchen, indem der zugehörige Aufruf von `jl_apply` inspiziert wird. Um ein Beispiel aus der realen Welt zu nehmen:

```
Breakpoint 1, jl_throw (e=0x7ffdf42de400) at task.c:802
802 {
(gdb) p jl_(e)
ErrorException("auto_unbox: unable to determine argument type")
$2 = void
(gdb) bt 10
#0  jl_throw (e=0x7ffdf42de400) at task.c:802
#1  0x00007ffff65412fe in jl_error (str=0x7ffde56be000 <_j_str267> "auto_unbox:
   unable to determine argument type")
   at builtins.c:39
#2  0x00007ffde56bd01a in julia_convert_16886 ()
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
...
```

Der aktuellste `jl_apply` befindet sich im Frame #3, also können wir dorthin zurückgehen und den AST für die Funktion `julia_convert_16886` betrachten. Dies ist der eindeutige Name für eine Methode von `convert`. `f` in diesem Frame ist ein `jl_function_t*`, also können wir die Typsignatur, falls vorhanden, aus dem Feld `specTypes` betrachten:

```
(gdb) f 3
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
1281            return f->fptr((jl_value_t*)f, args, nargs);
(gdb) p f->linfo->specTypes
$4 = (jl_tupletype_t *) 0x7ffdf39b1030
(gdb) p jl_( f->linfo->specTypes )
Tuple{Type{Float32}, Float64}           # <-- type signature for julia_convert_16886
```

Dann können wir uns den AST für diese Funktion ansehen:

```
(gdb) p jl_( jl_uncompress_ast(f->linfo, f->linfo->ast) )
Expr(:lambda, Array{Any, 1}[:#s29, :x], Array{Any, 1}[Array{Any, 1}[], Array{Any, 1}[Array{Any, 1}[:#s29, :Any, 0], Array{Any, 1}[:x, :Any, 0]], Array{Any, 1}[], 0], Expr(:body,
Expr(:line, 90, :float.jl)::Any,
Expr(:return, Expr(:call, :box, :Float32, Expr(:call, :fptrunc, :Float32, :x)::Any)::Any)::Any)::Any)::Any
```

Schließlich, und vielleicht am nützlichsten, können wir die Funktion zwingen, neu kompiliert zu werden, um den Codegenerierungsprozess Schritt für Schritt zu durchlaufen. Dazu löschen Sie das zwischengespeicherte `functionObject` aus dem `jl_lamdbda_info_t*`:

```
(gdb) p f->linfo->functionObject
$8 = (void *) 0x1289d070
(gdb) set f->linfo->functionObject = NULL
```

Setzen Sie dann einen Haltepunkt an einer nützlichen Stelle (z. B. `emit_function`, `emit_expr`, `emit_call` usw.) und führen Sie die Codegenerierung aus:

```
(gdb) p jl_compile(f)
... # your breakpoint here
```

## Debugging precompilation errors

Modul-Vorcompilation startet einen separaten Julia-Prozess, um jedes Modul vorzukompilieren. Einen Haltepunkt zu setzen oder Fehler in einem Vorcompilierungsarbeiter zu erfassen, erfordert das Anheften eines Debuggers an den Arbeiter. Der einfachste Ansatz besteht darin, den Debugger so einzustellen, dass er auf neue Prozessstarts mit einem bestimmten Namen achtet. Zum Beispiel:

```
(gdb) attach -w -n julia-debug
```

oder:

```
(lldb) process attach -w -n julia-debug
```

Führen Sie dann ein Skript/einen Befehl aus, um die Vorcompilierung zu starten. Wie zuvor beschrieben, verwenden Sie bedingte Haltepunkte im übergeordneten Prozess, um spezifische Datei-Ladevorgänge zu erfassen und das Debugging-Fenster einzugrenzen. (Einige Betriebssysteme erfordern möglicherweise alternative Ansätze, wie das Verfolgen jedes `fork` vom übergeordneten Prozess aus.)

## Mozilla's Record and Replay Framework (rr)

Julia funktioniert jetzt direkt mit [rr](https://rr-project.org/), dem leichten Aufzeichnungs- und deterministischen Debugging-Framework von Mozilla. Dies ermöglicht es Ihnen, den Verlauf einer Ausführung deterministisch wiederzugeben. Die Adressräume, Registerinhalte, Syscall-Daten usw. der wiedergegebenen Ausführung sind in jedem Durchlauf genau gleich.

Eine aktuelle Version von rr (3.1.0 oder höher) ist erforderlich.

### Reproducing concurrency bugs with rr

rr simuliert standardmäßig eine einsträngige Maschine. Um parallelen Code zu debuggen, können Sie `rr record --chaos` verwenden, was dazu führt, dass rr zwischen einem und acht Kernen simuliert, die zufällig ausgewählt werden. Sie möchten daher möglicherweise `JULIA_NUM_THREADS=8` setzen und Ihren Code unter rr erneut ausführen, bis Sie Ihren Fehler gefunden haben.
