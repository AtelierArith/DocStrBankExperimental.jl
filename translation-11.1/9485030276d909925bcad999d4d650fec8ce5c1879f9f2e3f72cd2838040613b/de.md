# Embedding Julia

Wie wir in [Calling C and Fortran Code](@ref) gesehen haben, bietet Julia eine einfache und effiziente Möglichkeit, Funktionen, die in C geschrieben sind, aufzurufen. Es gibt jedoch Situationen, in denen das Gegenteil erforderlich ist: Julia-Funktionen aus C-Code aufzurufen. Dies kann verwendet werden, um Julia-Code in ein größeres C/C++-Projekt zu integrieren, ohne alles in C/C++ neu schreiben zu müssen. Julia hat eine C-API, um dies zu ermöglichen. Da fast alle Programmiersprachen eine Möglichkeit haben, C-Funktionen aufzurufen, kann die Julia C-API auch verwendet werden, um weitere Sprachbrücken zu bauen (z. B. Julia aus Python, Rust oder C# aufzurufen). Obwohl Rust und C++ die C-Embedding-API direkt verwenden können, haben beide Pakete, die dabei helfen, für C++ ist [Jluna](https://github.com/Clemapfel/jluna) nützlich.

## High-Level Embedding

**Hinweis**: Dieser Abschnitt behandelt das Einbetten von Julia-Code in C auf Unix-ähnlichen Betriebssystemen. Für die Durchführung auf Windows siehe bitte den folgenden Abschnitt, [High-Level Embedding on Windows with Visual Studio](@ref).

Wir beginnen mit einem einfachen C-Programm, das Julia initialisiert und einige Julia-Code aufruft:

```c
#include <julia.h>
JULIA_DEFINE_FAST_TLS // only define this once, in an executable (not in a shared library) if you want fast code.

int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

Um dieses Programm zu erstellen, müssen Sie den Pfad zu den Julia-Headern zum Include-Pfad hinzufügen und gegen `libjulia` verlinken. Wenn Julia beispielsweise in `$JULIA_DIR` installiert ist, kann das obige Testprogramm `test.c` mit `gcc` wie folgt kompiliert werden:

```
gcc -o test -fPIC -I$JULIA_DIR/include/julia -L$JULIA_DIR/lib -Wl,-rpath,$JULIA_DIR/lib test.c -ljulia
```

Alternativ können Sie das `embedding.c`-Programm im Julia-Quellbaum im Ordner `test/embedding/` ansehen. Die Datei `cli/loader_exe.c` ist ein weiteres einfaches Beispiel dafür, wie man `jl_options`-Optionen beim Verlinken mit `libjulia` festlegt.

Die erste Sache, die getan werden muss, bevor eine andere Julia C-Funktion aufgerufen wird, ist die Initialisierung von Julia. Dies geschieht durch den Aufruf von `jl_init`, der versucht, den Installationsort von Julia automatisch zu bestimmen. Wenn Sie einen benutzerdefinierten Speicherort angeben oder angeben müssen, welches System-Image geladen werden soll, verwenden Sie stattdessen `jl_init_with_image`.

Die zweite Anweisung im Testprogramm bewertet eine Julia-Anweisung mithilfe eines Aufrufs an `jl_eval_string`.

Bevor das Programm beendet wird, wird dringend empfohlen, dass `jl_atexit_hook` aufgerufen wird. Das obige Beispielprogramm ruft dies kurz vor der Rückkehr aus `main` auf.

!!! note
    Derzeit erfordert das dynamische Verlinken mit der `libjulia`-Shared Library das Übergeben der `RTLD_GLOBAL`-Option. In Python sieht das so aus:

    ```
    >>> julia=CDLL('./libjulia.dylib',RTLD_GLOBAL)
    >>> julia.jl_init.argtypes = []
    >>> julia.jl_init()
    250593296
    ```


!!! note
    Wenn das Julia-Programm auf Symbole aus der Hauptanwendung zugreifen muss, kann es notwendig sein, das Linker-Flag `-Wl,--export-dynamic` zur Compile-Zeit unter Linux hinzuzufügen, zusätzlich zu den von `julia-config.jl` generierten. Dies ist beim Kompilieren einer Shared Library nicht erforderlich.


### Using julia-config to automatically determine build parameters

Das Skript `julia-config.jl` wurde erstellt, um zu bestimmen, welche Build-Parameter von einem Programm benötigt werden, das eingebettetes Julia verwendet. Dieses Skript verwendet die Build-Parameter und die Systemkonfiguration der spezifischen Julia-Distribution, von der es aufgerufen wird, um die erforderlichen Compiler-Flags für ein Einbettungsprogramm zu exportieren, das mit dieser Distribution interagiert. Dieses Skript befindet sich im gemeinsamen Datenverzeichnis von Julia.

#### Example

```c
#include <julia.h>

int main(int argc, char *argv[])
{
    jl_init();
    (void)jl_eval_string("println(sqrt(2.0))");
    jl_atexit_hook(0);
    return 0;
}
```

#### On the command line

Eine einfache Verwendung dieses Skripts erfolgt über die Befehlszeile. Vorausgesetzt, dass sich `julia-config.jl` in `/usr/local/julia/share/julia` befindet, kann es direkt über die Befehlszeile aufgerufen werden und akzeptiert jede Kombination aus drei Flags:

```
/usr/local/julia/share/julia/julia-config.jl
Usage: julia-config [--cflags|--ldflags|--ldlibs]
```

Wenn das obige Beispiel in der Datei `embed_example.c` gespeichert ist, wird der folgende Befehl es in ein ausführbares Programm unter Linux und Windows (MSYS2-Umgebung) kompilieren. Unter macOS ersetzen Sie `gcc` durch `clang`.

```
/usr/local/julia/share/julia/julia-config.jl --cflags --ldflags --ldlibs | xargs gcc embed_example.c
```

#### Use in Makefiles

Im Allgemeinen werden Einbettungsprojekte komplizierter sein als das obige Beispiel, und daher ermöglicht das Folgende auch allgemeine Makefile-Unterstützung – vorausgesetzt, GNU Make wird aufgrund der Verwendung der **shell**-Makroerweiterungen verwendet. Darüber hinaus, obwohl `julia-config.jl` normalerweise im Verzeichnis `/usr/local` zu finden ist, kann Julia selbst verwendet werden, um `julia-config.jl` zu finden, und das Makefile kann davon profitieren. Das obige Beispiel wird erweitert, um ein Makefile zu verwenden:

```
JL_SHARE = $(shell julia -e 'print(joinpath(Sys.BINDIR, Base.DATAROOTDIR, "julia"))')
CFLAGS   += $(shell $(JL_SHARE)/julia-config.jl --cflags)
CXXFLAGS += $(shell $(JL_SHARE)/julia-config.jl --cflags)
LDFLAGS  += $(shell $(JL_SHARE)/julia-config.jl --ldflags)
LDLIBS   += $(shell $(JL_SHARE)/julia-config.jl --ldlibs)

all: embed_example
```

Jetzt ist der Build-Befehl einfach `make`.

## High-Level Embedding on Windows with Visual Studio

Wenn die Umgebungsvariable `JULIA_DIR` nicht eingerichtet ist, fügen Sie sie über das System-Panel hinzu, bevor Sie Visual Studio starten. Der `bin`-Ordner unter JULIA_DIR sollte im System-PATH enthalten sein.

Wir beginnen damit, Visual Studio zu öffnen und ein neues Konsolenanwendungsprojekt zu erstellen. Öffnen Sie die Header-Datei 'stdafx.h' und fügen Sie am Ende die folgenden Zeilen hinzu:

```c
#include <julia.h>
```

Dann ersetzen Sie die main() Funktion im Projekt mit diesem Code:

```c
int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

Der nächste Schritt besteht darin, das Projekt so einzurichten, dass die Julia-Headerdateien und die Bibliotheken gefunden werden. Es ist wichtig zu wissen, ob die Julia-Installation 32- oder 64-Bit ist. Entfernen Sie alle Plattformkonfigurationen, die nicht mit der Julia-Installation übereinstimmen, bevor Sie fortfahren.

Verwenden Sie den Projekt-Eigenschaften-Dialog, um zu `C/C++` | `Allgemein` zu gehen und `$(JULIA_DIR)\include\julia\` zu den zusätzlichen Include-Verzeichnissen hinzuzufügen. Gehen Sie dann zum Abschnitt `Linker` | `Allgemein` und fügen Sie `$(JULIA_DIR)\lib` zu den zusätzlichen Bibliotheksverzeichnissen hinzu. Fügen Sie schließlich unter `Linker` | `Eingabe` `libjulia.dll.a;libopenlibm.dll.a;` zur Liste der Bibliotheken hinzu.

An diesem Punkt sollte das Projekt erstellt und ausgeführt werden.

## Converting Types

Echte Anwendungen müssen nicht nur Ausdrücke ausführen, sondern auch deren Werte an das Host-Programm zurückgeben. `jl_eval_string` gibt einen `jl_value_t*` zurück, der ein Zeiger auf ein im Heap zugewiesenes Julia-Objekt ist. Das Speichern einfacher Datentypen wie [`Float64`](@ref) auf diese Weise wird als `boxing` bezeichnet, und das Extrahieren der gespeicherten primitiven Daten wird als `unboxing` bezeichnet. Unser verbessertes Beispielprogramm, das die Quadratwurzel von 2 in Julia berechnet und das Ergebnis in C zurückliest, enthält nun diesen Code:

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");

if (jl_typeis(ret, jl_float64_type)) {
    double ret_unboxed = jl_unbox_float64(ret);
    printf("sqrt(2.0) in C: %e \n", ret_unboxed);
}
else {
    printf("ERROR: unexpected return type from sqrt(::Float64)\n");
}
```

Um zu überprüfen, ob `ret` von einem bestimmten Julia-Typ ist, können wir die Funktionen `jl_isa`, `jl_typeis` oder `jl_is_...` verwenden. Indem wir `typeof(sqrt(2.0))` in die Julia-Shell eingeben, können wir sehen, dass der Rückgabewert der Typ [`Float64`](@ref) (`double` in C) ist. Um den verpackten Julia-Wert in einen C-Doppelwert zu konvertieren, wird in dem obigen Code-Snippet die Funktion `jl_unbox_float64` verwendet.

Entsprechende `jl_box_...` Funktionen werden verwendet, um in die andere Richtung zu konvertieren:

```c
jl_value_t *a = jl_box_float64(3.0);
jl_value_t *b = jl_box_float32(3.0f);
jl_value_t *c = jl_box_int32(3);
```

Wie wir als Nächstes sehen werden, ist Boxing erforderlich, um Julia-Funktionen mit spezifischen Argumenten aufzurufen.

## Calling Julia Functions

Während `jl_eval_string` es C ermöglicht, das Ergebnis eines Julia-Ausdrucks zu erhalten, erlaubt es nicht, in C berechnete Argumente an Julia zu übergeben. Dazu müssen Sie Julia-Funktionen direkt aufrufen, indem Sie `jl_call` verwenden:

```c
jl_function_t *func = jl_get_function(jl_base_module, "sqrt");
jl_value_t *argument = jl_box_float64(2.0);
jl_value_t *ret = jl_call1(func, argument);
```

Im ersten Schritt wird ein Handle zur Julia-Funktion `sqrt` abgerufen, indem `jl_get_function` aufgerufen wird. Das erste Argument, das an `jl_get_function` übergeben wird, ist ein Zeiger auf das `Base`-Modul, in dem `sqrt` definiert ist. Dann wird der Double-Wert mit `jl_box_float64` verpackt. Schließlich wird im letzten Schritt die Funktion mit `jl_call1` aufgerufen. Es existieren auch die Funktionen `jl_call0`, `jl_call2` und `jl_call3`, um bequem mit unterschiedlichen Argumentanzahlen umzugehen. Um mehr Argumente zu übergeben, verwenden Sie `jl_call`:

```
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs)
```

Sein zweites Argument `args` ist ein Array von `jl_value_t*`-Argumenten und `nargs` ist die Anzahl der Argumente.

Es gibt auch eine alternative, möglicherweise einfachere Möglichkeit, Julia-Funktionen aufzurufen, und zwar über [`@cfunction`](@ref). Die Verwendung von `@cfunction` ermöglicht es Ihnen, die Typkonvertierungen auf der Julia-Seite durchzuführen, was typischerweise einfacher ist, als sie auf der C-Seite durchzuführen. Das obige Beispiel `sqrt` würde mit `@cfunction` so geschrieben werden:

```c
double (*sqrt_jl)(double) = jl_unbox_voidpointer(jl_eval_string("@cfunction(sqrt, Float64, (Float64,))"));
double ret = sqrt_jl(2.0);
```

wo wir zuerst eine C-aufrufbare Funktion in Julia definieren, den Funktionszeiger daraus extrahieren und schließlich aufrufen. Neben der Vereinfachung von Typkonvertierungen, indem diese in der höherstufigen Sprache durchgeführt werden, beseitigt der Aufruf von Julia-Funktionen über `@cfunction`-Zeiger den dynamischen Dispatch-Overhead, der für `jl_call` erforderlich ist (bei dem alle Argumente "verpackt" sind), und sollte eine Leistung haben, die der von nativen C-Funktionszeigern entspricht.

## Memory Management

Wie wir gesehen haben, werden Julia-Objekte in C als Zeiger vom Typ `jl_value_t*` dargestellt. Dies wirft die Frage auf, wer für das Freigeben dieser Objekte verantwortlich ist.

Typischerweise werden Julia-Objekte vom Garbage Collector (GC) freigegeben, aber der GC weiß nicht automatisch, dass wir eine Referenz auf einen Julia-Wert aus C halten. Das bedeutet, dass der GC Objekte unter Ihnen freigeben kann, wodurch Zeiger ungültig werden.

Die GC wird nur ausgeführt, wenn neue Julia-Objekte zugewiesen werden. Aufrufe wie `jl_box_float64` führen zu Zuweisungen, aber Zuweisungen können auch zu jedem Zeitpunkt beim Ausführen von Julia-Code auftreten.

Beim Schreiben von Code, der Julia einbettet, ist es im Allgemeinen sicher, `jl_value_t*`-Werte zwischen `jl_...`-Aufrufen zu verwenden (da der GC nur durch diese Aufrufe ausgelöst wird). Um jedoch sicherzustellen, dass Werte `jl_...`-Aufrufe überstehen können, müssen wir Julia mitteilen, dass wir weiterhin eine Referenz auf Julia [root](https://www.cs.purdue.edu/homes/hosking/690M/p611-fenichel.pdf)-Werte halten, ein Prozess, der als "GC-Rooting" bezeichnet wird. Das Rooten eines Wertes stellt sicher, dass der Garbage Collector diesen Wert nicht versehentlich als ungenutzt identifiziert und den Speicher, der diesen Wert unterstützt, freigibt. Dies kann mit den `JL_GC_PUSH`-Makros erfolgen:

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret);
// Do something with ret
JL_GC_POP();
```

Der `JL_GC_POP`-Aufruf gibt die durch den vorherigen `JL_GC_PUSH` hergestellten Referenzen frei. Beachten Sie, dass `JL_GC_PUSH` Referenzen auf dem C-Stack speichert, sodass es genau mit einem `JL_GC_POP` gepaart werden muss, bevor der Gültigkeitsbereich verlassen wird. Das heißt, bevor die Funktion zurückkehrt oder der Kontrollfluss anderweitig den Block verlässt, in dem `JL_GC_PUSH` aufgerufen wurde.

Mehrere Julia-Werte können gleichzeitig mit den Makros `JL_GC_PUSH2` bis `JL_GC_PUSH6` hinzugefügt werden:

```
JL_GC_PUSH2(&ret1, &ret2);
// ...
JL_GC_PUSH6(&ret1, &ret2, &ret3, &ret4, &ret5, &ret6);
```

Um ein Array von Julia-Werten zu pushen, kann man das `JL_GC_PUSHARGS`-Makro verwenden, das wie folgt verwendet werden kann:

```c
jl_value_t **args;
JL_GC_PUSHARGS(args, 2); // args can now hold 2 `jl_value_t*` objects
args[0] = some_value;
args[1] = some_other_value;
// Do something with args (e.g. call jl_... functions)
JL_GC_POP();
```

Jeder Geltungsbereich muss nur einen Aufruf von `JL_GC_PUSH*` haben und sollte nur mit einem einzigen `JL_GC_POP`-Aufruf gepaart sein. Wenn nicht alle notwendigen Variablen, die Sie verankern möchten, mit einem einzigen Aufruf von `JL_GC_PUSH*` gepusht werden können oder wenn mehr als 6 Variablen gepusht werden müssen und die Verwendung eines Argumentarrays keine Option ist, kann man innere Blöcke verwenden:

```c
jl_value_t *ret1 = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret1);
jl_value_t *ret2 = 0;
{
    jl_function_t *func = jl_get_function(jl_base_module, "exp");
    ret2 = jl_call1(func, ret1);
    JL_GC_PUSH1(&ret2);
    // Do something with ret2.
    JL_GC_POP();    // This pops ret2.
}
JL_GC_POP();    // This pops ret1.
```

Beachten Sie, dass es nicht notwendig ist, gültige `jl_value_t*`-Werte zu haben, bevor Sie `JL_GC_PUSH*` aufrufen. Es ist in Ordnung, eine Anzahl von ihnen auf `NULL` zu initialisieren, diese an `JL_GC_PUSH*` zu übergeben und dann die tatsächlichen Julia-Werte zu erstellen. Zum Beispiel:

```
jl_value_t *ret1 = NULL, *ret2 = NULL;
JL_GC_PUSH2(&ret1, &ret2);
ret1 = jl_eval_string("sqrt(2.0)");
ret2 = jl_eval_string("sqrt(3.0)");
// Use ret1 and ret2
JL_GC_POP();
```

Wenn es erforderlich ist, den Zeiger auf eine Variable zwischen Funktionen (oder Blockbereichen) zu halten, ist es nicht möglich, `JL_GC_PUSH*` zu verwenden. In diesem Fall ist es notwendig, eine Referenz auf die Variable im globalen Julia-Scope zu erstellen und zu behalten. Eine einfache Möglichkeit, dies zu erreichen, besteht darin, ein globales `IdDict` zu verwenden, das die Referenzen speichert und eine Deallokation durch den GC vermeidet. Diese Methode funktioniert jedoch nur ordnungsgemäß mit veränderlichen Typen.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Vector{Float64}`, which is mutable.
var = jl_eval_string("[sqrt(2.0); sqrt(4.0); sqrt(6.0)]");

// To protect `var`, add its reference to `refs`.
jl_call3(setindex, refs, var, var);
```

Wenn die Variable unveränderlich ist, muss sie in einen entsprechenden veränderlichen Container oder vorzugsweise in ein `RefValue{Any}` eingewickelt werden, bevor sie in `IdDict` eingefügt wird. In diesem Ansatz muss der Container über C-Code erstellt oder gefüllt werden, zum Beispiel mit der Funktion `jl_new_struct`. Wenn der Container mit `jl_call*` erstellt wird, müssen Sie den Zeiger neu laden, um ihn im C-Code verwenden zu können.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");
jl_datatype_t* reft = (jl_datatype_t*)jl_eval_string("Base.RefValue{Any}");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Float64`, which is immutable.
var = jl_eval_string("sqrt(2.0)");

// Protect `var` until we add its reference to `refs`.
JL_GC_PUSH1(&var);

// Wrap `var` in `RefValue{Any}` and push to `refs` to protect it.
jl_value_t* rvar = jl_new_struct(reft, var);
JL_GC_POP();

jl_call3(setindex, refs, rvar, rvar);
```

Der GC kann erlaubt werden, eine Variable freizugeben, indem die Referenz darauf aus `refs` mit der Funktion `delete!` entfernt wird, vorausgesetzt, dass keine andere Referenz auf die Variable irgendwo gehalten wird:

```c
jl_function_t* delete = jl_get_function(jl_base_module, "delete!");
jl_call2(delete, refs, rvar);
```

Als Alternative für sehr einfache Fälle ist es möglich, einfach einen globalen Container vom Typ `Vector{Any}` zu erstellen und die Elemente bei Bedarf daraus abzurufen, oder sogar eine globale Variable pro Zeiger zu erstellen, indem man

```c
jl_module_t *mod = jl_main_module;
jl_sym_t *var = jl_symbol("var");
jl_binding_t *bp = jl_get_binding_wr(mod, var, 1);
jl_checked_assignment(bp, mod, var, val);
```

### Updating fields of GC-managed objects

Der Garbage Collector geht auch davon aus, dass er über jedes Objekt der älteren Generation informiert ist, das auf ein Objekt der jüngeren Generation zeigt. Jedes Mal, wenn ein Zeiger aktualisiert wird und diese Annahme verletzt wird, muss dies dem Collector mit der Funktion `jl_gc_wb` (Write Barrier) signalisiert werden, und zwar wie folgt:

```c
jl_value_t *parent = some_old_value, *child = some_young_value;
((some_specific_type*)parent)->field = child;
jl_gc_wb(parent, child);
```

Es ist im Allgemeinen unmöglich vorherzusagen, welche Werte zur Laufzeit alt sein werden, daher muss die Schreibsperre nach allen expliziten Zuweisungen eingefügt werden. Eine bemerkenswerte Ausnahme ist, wenn das `parent`-Objekt gerade zugewiesen wurde und seitdem keine Garbage Collection stattgefunden hat. Beachten Sie, dass die meisten `jl_...`-Funktionen manchmal eine Garbage Collection auslösen können.

Die Schreibsperre ist auch notwendig für Arrays von Zeigern, wenn ihre Daten direkt aktualisiert werden. Der Aufruf von `jl_array_ptr_set` wird in der Regel viel bevorzugt. Aber direkte Aktualisierungen können durchgeführt werden. Zum Beispiel:

```c
jl_array_t *some_array = ...; // e.g. a Vector{Any}
void **data = jl_array_data(some_array, void*);
jl_value_t *some_value = ...;
data[0] = some_value;
jl_gc_wb(jl_array_owner(some_array), some_value);
```

### Controlling the Garbage Collector

Es gibt einige Funktionen zur Steuerung des GC. In normalen Anwendungsfällen sollten diese nicht erforderlich sein.

| Function             | Description                                  |
|:-------------------- |:-------------------------------------------- |
| `jl_gc_collect()`    | Force a GC run                               |
| `jl_gc_enable(0)`    | Disable the GC, return previous state as int |
| `jl_gc_enable(1)`    | Enable the GC,  return previous state as int |
| `jl_gc_is_enabled()` | Return current state as int                  |

## Working with Arrays

Julia und C können Array-Daten ohne Kopieren teilen. Das nächste Beispiel zeigt, wie das funktioniert.

Julia-Arrays werden in C durch den Datentyp `jl_array_t*` dargestellt. Grundsätzlich ist `jl_array_t` eine Struktur, die enthält:

  * Information über den Datentyp
  * Ein Zeiger auf den Datenblock
  * Information über die Größen des Arrays

Um die Dinge einfach zu halten, beginnen wir mit einem 1D-Array. Ein Array mit Float64-Elementen der Länge 10 kann wie folgt erstellt werden:

```c
jl_value_t* array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 1);
jl_array_t* x          = jl_alloc_array_1d(array_type, 10);
```

Alternativ können Sie, wenn Sie das Array bereits zugewiesen haben, einen dünnen Wrapper um dessen Daten erstellen:

```c
double *existingArray = (double*)malloc(sizeof(double)*10);
jl_array_t *x = jl_ptr_to_array_1d(array_type, existingArray, 10, 0);
```

Das letzte Argument ist ein Boolean, der angibt, ob Julia das Eigentum an den Daten übernehmen soll. Wenn dieses Argument ungleich null ist, wird der GC `free` auf den Datenzeiger aufrufen, wenn das Array nicht mehr referenziert wird.

Um auf die Daten von `x` zuzugreifen, können wir `jl_array_data` verwenden:

```c
double *xData = jl_array_data(x, double);
```

Jetzt können wir das Array füllen:

```c
for (size_t i = 0; i < jl_array_nrows(x); i++)
    xData[i] = i;
```

Jetzt lassen Sie uns eine Julia-Funktion aufrufen, die eine In-Place-Operation auf `x` durchführt:

```c
jl_function_t *func = jl_get_function(jl_base_module, "reverse!");
jl_call1(func, (jl_value_t*)x);
```

Durch das Drucken des Arrays kann man überprüfen, dass die Elemente von `x` jetzt umgekehrt sind.

### Accessing Returned Arrays

Wenn eine Julia-Funktion ein Array zurückgibt, kann der Rückgabewert von `jl_eval_string` und `jl_call` in ein `jl_array_t*` umgewandelt werden:

```c
jl_function_t *func  = jl_get_function(jl_base_module, "reverse");
jl_array_t *y = (jl_array_t*)jl_call1(func, (jl_value_t*)x);
```

Jetzt kann der Inhalt von `y` wie zuvor mit `jl_array_data` zugegriffen werden. Wie immer sollten Sie eine Referenz auf das Array behalten, während es verwendet wird.

### Multidimensional Arrays

Julias mehrdimensionale Arrays werden im Speicher in Spalten-Hauptreihenfolge gespeichert. Hier ist ein Code, der ein 2D-Array erstellt und dessen Eigenschaften abruft:

```c
// Create 2D array of float64 type
jl_value_t *array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 2);
int dims[] = {10,5};
jl_array_t *x  = jl_alloc_array_nd(array_type, dims, 2);

// Get array pointer
double *p = jl_array_data(x, double);
// Get number of dimensions
int ndims = jl_array_ndims(x);
// Get the size of the i-th dim
size_t size0 = jl_array_dim(x,0);
size_t size1 = jl_array_dim(x,1);

// Fill array with data
for(size_t i=0; i<size1; i++)
    for(size_t j=0; j<size0; j++)
        p[j + size0*i] = i + j;
```

Beachten Sie, dass Julia-Arrays 1-basierte Indizes verwenden, während die C-API 0-basierte Indizes verwendet (zum Beispiel beim Aufrufen von `jl_array_dim`), um als idiomatischer C-Code zu gelten.

## Exceptions

Julia-Code kann Ausnahmen auslösen. Zum Beispiel:

```c
jl_eval_string("this_function_does_not_exist()");
```

Dieser Aufruf scheint nichts zu tun. Es ist jedoch möglich zu überprüfen, ob eine Ausnahme ausgelöst wurde:

```c
if (jl_exception_occurred())
    printf("%s \n", jl_typeof_str(jl_exception_occurred()));
```

Wenn Sie die Julia C API aus einer Sprache verwenden, die Ausnahmen unterstützt (z. B. Python, C#, C++), ist es sinnvoll, jeden Aufruf an `libjulia` in eine Funktion zu kapseln, die überprüft, ob eine Ausnahme ausgelöst wurde, und dann die Ausnahme in der Host-Sprache erneut auslöst.

### Throwing Julia Exceptions

Wenn Sie aufrufbare Funktionen in Julia schreiben, kann es notwendig sein, Argumente zu validieren und Ausnahmen auszulösen, um Fehler anzuzeigen. Eine typische Typüberprüfung sieht folgendermaßen aus:

```c
if (!jl_typeis(val, jl_float64_type)) {
    jl_type_error(function_name, (jl_value_t*)jl_float64_type, val);
}
```

Allgemeine Ausnahmen können mit den Funktionen ausgelöst werden:

```c
void jl_error(const char *str);
void jl_errorf(const char *fmt, ...);
```

`jl_error` nimmt einen C-String, und `jl_errorf` wird wie `printf` aufgerufen:

```c
jl_errorf("argument x = %d is too large", x);
```

wo in diesem Beispiel wird angenommen, dass `x` eine ganze Zahl ist.

### Thread-safety

Im Allgemeinen ist die Julia C-API nicht vollständig threadsicher. Beim Einbetten von Julia in eine multithreaded Anwendung muss darauf geachtet werden, die folgenden Einschränkungen nicht zu verletzen:

  * `jl_init()` darf nur einmal während der Lebensdauer der Anwendung aufgerufen werden. Das gleiche gilt für `jl_atexit_hook()`, und es darf nur nach `jl_init()` aufgerufen werden.
  * `jl_...()` API-Funktionen dürfen nur aus dem Thread aufgerufen werden, in dem `jl_init()` aufgerufen wurde, *oder von Threads, die vom Julia-Laufzeitsystem gestartet wurden*. Das Aufrufen von Julia-API-Funktionen aus vom Benutzer gestarteten Threads wird nicht unterstützt und kann zu undefiniertem Verhalten und Abstürzen führen.

Die zweite Bedingung oben impliziert, dass Sie `jl_...()`-Funktionen nicht sicher aus Threads aufrufen können, die nicht von Julia gestartet wurden (der Thread, der `jl_init()` aufruft, ist die Ausnahme). Zum Beispiel wird Folgendes nicht unterstützt und wird höchstwahrscheinlich zu einem Segfault führen:

```c
void *func(void*)
{
    // Wrong, jl_eval_string() called from thread that was not started by Julia
    jl_eval_string("println(Threads.threadid())");
    return NULL;
}

int main()
{
    pthread_t t;

    jl_init();

    // Start a new thread
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);

    jl_atexit_hook(0);
}
```

Stattdessen wird es funktionieren, alle Julia-Aufrufe aus demselben benutzerdefinierten Thread auszuführen:

```c
void *func(void*)
{
    // Okay, all jl_...() calls from the same thread,
    // even though it is not the main application thread
    jl_init();
    jl_eval_string("println(Threads.threadid())");
    jl_atexit_hook(0);
    return NULL;
}

int main()
{
    pthread_t t;
    // Create a new thread, which runs func()
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);
}
```

Ein Beispiel für den Aufruf der Julia C-API von einem Thread, der von Julia selbst gestartet wurde:

```c
#include <julia/julia.h>
JULIA_DEFINE_FAST_TLS

double c_func(int i)
{
    printf("[C %08x] i = %d\n", pthread_self(), i);

    // Call the Julia sqrt() function to compute the square root of i, and return it
    jl_function_t *sqrt = jl_get_function(jl_base_module, "sqrt");
    jl_value_t* arg = jl_box_int32(i);
    double ret = jl_unbox_float64(jl_call1(sqrt, arg));

    return ret;
}

int main()
{
    jl_init();

    // Define a Julia function func() that calls our c_func() defined in C above
    jl_eval_string("func(i) = ccall(:c_func, Float64, (Int32,), i)");

    // Call func() multiple times, using multiple threads to do so
    jl_eval_string("println(Threads.threadpoolsize())");
    jl_eval_string("use(i) = println(\"[J $(Threads.threadid())] i = $(i) -> $(func(i))\")");
    jl_eval_string("Threads.@threads for i in 1:5 use(i) end");

    jl_atexit_hook(0);
}
```

Wenn wir diesen Code mit 2 Julia-Threads ausführen, erhalten wir die folgende Ausgabe (Hinweis: Die Ausgabe variiert je nach Ausführung und System):

```sh
$ JULIA_NUM_THREADS=2 ./thread_example
2
[C 3bfd9c00] i = 1
[C 23938640] i = 4
[J 1] i = 1 -> 1.0
[C 3bfd9c00] i = 2
[J 1] i = 2 -> 1.4142135623730951
[C 3bfd9c00] i = 3
[J 2] i = 4 -> 2.0
[C 23938640] i = 5
[J 1] i = 3 -> 1.7320508075688772
[J 2] i = 5 -> 2.23606797749979
```

Wie zu sehen ist, entspricht Julia-Thread 1 der pthread-ID 3bfd9c00, und Julia-Thread 2 entspricht der ID 23938640, was zeigt, dass tatsächlich mehrere Threads auf C-Ebene verwendet werden und dass wir die Julia-C-API-Routinen sicher von diesen Threads aus aufrufen können.
