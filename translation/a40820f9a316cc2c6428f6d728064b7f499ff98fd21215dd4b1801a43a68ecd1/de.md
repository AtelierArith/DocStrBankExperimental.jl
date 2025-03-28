# [Proper maintenance and care of multi-threading locks](@id Proper-maintenance-and-care-of-multi-threading-locks)

Die folgenden Strategien werden verwendet, um sicherzustellen, dass der Code frei von Deadlocks ist (insbesondere durch die Behebung der 4. Coffman-Bedingung: zirkuläres Warten).

> 1. Strukturieren Sie den Code so, dass jeweils nur ein Lock erworben werden muss.
> 2. erwerben Sie immer gemeinsame Sperren in derselben Reihenfolge, wie in der folgenden Tabelle angegeben
> 3. vermeiden Sie Konstrukte, die erwarten, dass unbeschränkte Rekursion erforderlich ist


## Locks

Unten sind alle Schlösser, die im System existieren, sowie die Mechanismen zu ihrer Verwendung, die das Potenzial für Deadlocks vermeiden (kein Strauß-Algorithmus hier erlaubt):

Die folgenden sind definitiv Blatt-Sperren (Stufe 1) und dürfen keine anderen Sperren zu erwerben versuchen:

>   * sichere Punkt
>
>     > Beachten Sie, dass dieses Schloss implizit von `JL_LOCK` und `JL_UNLOCK` erworben wird. Verwenden Sie die `_NOGC`-Varianten, um dies für Level-1-Schlösser zu vermeiden.
>     >
>     > Während Sie dieses Schloss halten, darf der Code keine Zuweisungen vornehmen oder auf Safepoints treffen. Beachten Sie, dass es Safepoints gibt, wenn Zuweisungen vorgenommen werden, GC aktiviert / deaktiviert wird, Ausnahme-Frames betreten / wiederhergestellt werden und Schlösser genommen / freigegeben werden.
>   * shared_map
>   * finalizers
>   * pagealloc
>   * gc*perm*lock
>   * flisp
>   * jl*in*stackwalk (Win32)
>   * ResourcePool<?>::mutex
>   * RLST_mutex
>   * llvm*Drucken*Mutex
>   * jl*gesperrter*stream::mutex
>   * debuginfo_asyncsafe
>   * inferenz*zeit*mutex
>   * ExecutionEngine::SessionLock
>
>     > flisp selbst ist bereits threadsicher, dieses Lock schützt nur den `jl_ast_context_list_t` Pool, ebenso schützen die ResourcePool<?>::mutexes nur den zugehörigen Ressourcenpool.


Der folgende ist ein Blattverschluss (Stufe 2) und erwirbt intern nur Sperren der Stufe 1 (Safepoint):

>   * global*roots*lock
>   * Modul->sperren
>   * JLDebuginfoPlugin::PluginMutex
>   * neu*abgeleitet*mutex


Der folgende ist ein Level-3-Schloss, das nur intern Level-1- oder Level-2-Schlösser erwerben kann:

>   * Methode->writelock
>   * typecache


Der folgende ist ein Level-4-Schloss, das nur rekursiv Level-1-, Level-2- oder Level-3-Schlösser erwerben kann:

>   * MethodTable->writelock


Kein Julia-Code darf aufgerufen werden, während an dieser Stelle ein Lock gehalten wird.

orc::ThreadSafeContext (TSCtx) Locks nehmen einen besonderen Platz in der Lock-Hierarchie ein. Sie werden verwendet, um den globalen nicht-thread-sicheren Zustand von LLVM zu schützen, aber es kann eine beliebige Anzahl von ihnen geben. Standardmäßig können all diese Locks als Level-5-Locks für den Vergleich mit dem Rest der Hierarchie behandelt werden. Das Erwerben eines TSCtx sollte nur aus dem Pool der TSCtxs des JIT erfolgen, und alle Locks auf diesem TSCtx sollten freigegeben werden, bevor er an den Pool zurückgegeben wird. Wenn mehrere TSCtx-Locks gleichzeitig erworben werden müssen (aufgrund rekursiver Kompilierung), sollten die Locks in der Reihenfolge erworben werden, in der die TSCtxs aus dem Pool entliehen wurden.

Der folgende ist ein Level 5 Schloss

>   * JuliaOJIT::EmissionMutex


Die folgenden sind ein Level-6-Schloss, das nur rekursiv auf niedrigere Ebenen zugreifen kann, um Schlösser zu erwerben:

>   * codegen
>   * jl*module*mutex


Der folgende ist ein fast Root-Lock (Level End-1), was bedeutet, dass nur der Root-Lock gehalten werden darf, wenn versucht wird, ihn zu erwerben:

>   * typeinf
>
>     > dies ist vielleicht einer der kniffligsten, da die Typinferenz von vielen Punkten aus aufgerufen werden kann
>     >
>     > Derzeit ist das Lock mit dem Codegen-Lock zusammengeführt, da sie sich gegenseitig rekursiv aufrufen.


Der folgende Lock synchronisiert IO-Operationen. Seien Sie sich bewusst, dass das Durchführen von I/O (zum Beispiel das Drucken von Warnmeldungen oder Debug-Informationen), während ein anderer oben aufgeführter Lock gehalten wird, zu tückischen und schwer zu findenden Deadlocks führen kann. SEIEN SIE SEHR VORSICHTIG!

>   * iolock
>   * Individuelle ThreadSynchronizers-Sperren
>
>     > dies kann weiterhin gehalten werden, nachdem das iolock freigegeben wurde, oder ohne es erworben werden, aber seien Sie sehr vorsichtig, niemals zu versuchen, das iolock zu erwerben, während Sie es halten.
>   * Libdl.LazyLibrary Sperre


Der folgende ist der Wurzelverschluss, was bedeutet, dass kein anderer Verschluss gehalten werden darf, wenn versucht wird, ihn zu erwerben:

>   * oberste Ebene
>
>     > dies sollte gehalten werden, während man versucht, eine Aktion auf oberster Ebene auszuführen (wie das Erstellen eines neuen Typs oder das Definieren einer neuen Methode): der Versuch, dieses Lock innerhalb einer gestuften Funktion zu erhalten, führt zu einer Deadlock-Bedingung!
>     >
>     > Zusätzlich ist unklar, ob *irgendein* Code sicher parallel mit einem beliebigen Top-Level-Ausdruck ausgeführt werden kann, sodass es möglicherweise erforderlich ist, dass alle Threads zuerst einen Safepoint erreichen.


## Broken Locks

Die folgenden Schlösser sind defekt:

  * oberste Ebene

    > existiert gerade nicht
    >
    > fix: erstelle es
  * Modul->sperren

    > Dies ist anfällig für Deadlocks, da nicht sichergestellt werden kann, dass es in der richtigen Reihenfolge erworben wird. Einige Operationen (wie `import_module`) fehlen ein Lock.
    >
    > fix: ersetzen mit `jl_modules_mutex`?
  * loading.jl: `require` und `register_root_module`

    > Diese Datei hat möglicherweise zahlreiche Probleme.
    >
    > fix: benötigt Schlösser

## Shared Global Data Structures

Diese Datenstrukturen benötigen jeweils Sperren, da sie einen gemeinsamen veränderbaren globalen Zustand darstellen. Es ist die umgekehrte Liste der oben genannten Sperrprioritäten. Diese Liste enthält keine Ressourcen der Stufe 1, da sie einfach sind.

MethodTable-Modifikationen (def, cache) : MethodTable->writelock

Typdeklarationen : Top-Level-Sperre

Typanwendung: typecache-Sperre

Globale Variablen Tabellen : Modul->sperren

Modul-Serializer: Top-Level-Sperre

JIT & Typinferenz : Codegenerierungssperre

MethodInstance/CodeInstance-Updates: Methode->writelock, codegen-Sperre

>   * Diese sind bei der Konstruktion festgelegt und unveränderlich:
>
>       * specTypen
>       * sparam_vals
>       * def
>       * Besitzer


>   * Diese werden von `jl_type_infer` festgelegt (während der Codegenerierungssperre):
>
>       * Cache
>       * rettype
>       * abgeleitet


```
    * valid ages
```

>   * `inInference`-Flag:
>
>       * Optimierung, um schnell zu vermeiden, dass `jl_type_infer` erneut aufgerufen wird, während es bereits läuft.
>       * Der aktuelle Zustand (des Setzens von `inferred`, dann `fptr`) ist durch den Codegenerierungssperre geschützt.


>   * Funktionszeiger:
>
>       * diese Übergänge einmal, von `NULL` zu einem Wert, während das Codegen-Sperre gehalten wird
>   * Code-Generator-Cache (der Inhalt von `functionObjectsDecls`):
>
>       * diese können mehrfach wechseln, aber nur solange der Codegen-Lock gehalten wird
>       * Es ist gültig, eine alte Version davon zu verwenden oder neue Versionen davon zu blockieren, sodass Rennen harmlos sind, solange der Code darauf achtet, keine anderen Daten in der Methodeninstanz (wie `rettype`) zu referenzieren und anzunehmen, dass sie koordiniert sind, es sei denn, der Codegen-Lock wird ebenfalls gehalten.


LLVMContext : Codegen-Sperre

Methode : Methode->writelock

  * Wurzeln Array (Serializer und Codegen)
  * aufrufen / spezialiserungen / tfunc änderungen
