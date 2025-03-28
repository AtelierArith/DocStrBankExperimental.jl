# Static analyzer annotations for GC correctness in C code

## Running the analysis

Das Analyse-Plugin, das die Analyse steuert, wird mit Julia ausgeliefert. Der Quellcode ist in `src/clangsa` zu finden. Um es auszuführen, muss die clang-Abhängigkeit gebaut werden. Setzen Sie die Variable `BUILD_LLVM_CLANG` in Ihrer Make.user, um eine geeignete Version von clang zu bauen. Sie möchten möglicherweise auch die vorgefertigten Binärdateien mit den Optionen `USE_BINARYBUILDER_LLVM` verwenden.

Alternativ (oder wenn diese nicht ausreichen), versuchen Sie

```sh
make -C src install-analysis-deps
```

aus Julias oberster Verzeichnis.

Danach ist es so einfach, die Analyse über den Quellbaum auszuführen, wie `make -C src analyzegc` auszuführen.

## General Overview

Da Julias GC präzise ist, muss sie korrekte Wurzelinformationen für jeden Wert aufrechterhalten, der zu jedem Zeitpunkt, an dem eine GC stattfinden kann, referenziert werden kann. Diese Stellen sind als `safepoints` bekannt, und im lokalen Kontext der Funktion erweitern wir diese Bezeichnung auf jeden Funktionsaufruf, der rekursiv an einem safepoint enden kann.

Im generierten Code wird dies automatisch durch den GC-Root-Platzierungsdurchgang (siehe das Kapitel über GC-Routing in den LLVM-Codegen-Entwicklungsdokumenten) behandelt. In C-Code müssen wir jedoch die Laufzeit manuell über alle GC-Wurzeln informieren. Dies geschieht mit den folgenden Makros:

```
// The value assigned to any slot passed as an argument to these
// is rooted for the duration of this GC frame.
JL_GC_PUSH{1,...,6}(args...)
// The values assigned into the size `n` array `rts` are rooted
// for the duration of this GC frame.
JL_GC_PUSHARGS(rts, n)
// Pop a GC frame
JL_GC_POP
```

Wenn diese Makros nicht dort verwendet werden, wo sie benötigt werden, oder sie falsch verwendet werden, führt dies zu stiller Speicherbeschädigung. Daher ist es sehr wichtig, dass sie korrekt in allen anwendbaren Codeabschnitten platziert werden.

Daher verwenden wir statische Analyse (insbesondere den Clang-Statische-Analyzer), um sicherzustellen, dass diese Makros korrekt verwendet werden. Der Rest dieses Dokuments gibt einen Überblick über diese statische Analyse und beschreibt die Unterstützung, die im Julia-Code-Basis benötigt wird, um die Dinge zum Laufen zu bringen.

## GC Invariants

Es gibt zwei einfache Invarianten der Korrektheit:

  * Alle `GC_PUSH`-Aufrufe müssen von einem entsprechenden `GC_POP` gefolgt werden (in der Praxis setzen wir dies auf Funktionsebene durch).
  * Wenn ein Wert zuvor an keinem Safepoint verankert war, wird er möglicherweise danach nicht mehr referenziert.

Natürlich liegt der Teufel im Detail. Um insbesondere die zweite der oben genannten Bedingungen zu erfüllen, müssen wir wissen:

  * Welche Aufrufe sind Safepoints und welche nicht
  * Welche Werte an einem bestimmten Safepoint verankert sind und welche nicht
  * Wann wird ein Wert referenziert

Für den zweiten Punkt insbesondere müssen wir wissen, welche Speicherorte zur Laufzeit als Wurzel betrachtet werden (d.h. Werte, die solchen Orten zugewiesen sind, sind verwurzelt). Dies umfasst Orte, die ausdrücklich als solche durch die Übergabe an eines der `GC_PUSH`-Makros, global verwurzelte Orte und Werte sowie jeden Ort, der rekursiv von einem dieser Orte erreichbar ist, bezeichnet sind.

## Static Analysis Algorithm

Die Idee selbst ist sehr einfach, obwohl die Implementierung deutlich komplizierter ist (hauptsächlich aufgrund einer großen Anzahl von Sonderfällen und Feinheiten von C und C++). Im Wesentlichen verfolgen wir alle Standorte, die verwurzelt sind, alle Werte, die verwurzelbar sind, und jede Ausdruck (Zuweisungen, Allokationen usw.), die die Verwurzelung von irgendwelchen verwurzelbaren Werten beeinflusst. Dann führen wir an jedem Safepoint eine "symbolische GC" durch und vergiften alle Werte, die an diesem Standort nicht verwurzelt sind. Wenn diese Werte später referenziert werden, geben wir einen Fehler aus.

Der Clang-Static-Analyzer funktioniert, indem er einen Graphen von Zuständen erstellt und diesen Graphen auf Fehlerquellen untersucht. Mehrere Knoten in diesem Graphen werden vom Analyzer selbst generiert (z. B. für den Kontrollfluss), aber die obigen Definitionen erweitern diesen Graphen mit unserem eigenen Zustand.

Der statische Analyzer ist interprozedural und kann den Kontrollfluss über Funktionsgrenzen hinweg analysieren. Der statische Analyzer ist jedoch nicht vollständig rekursiv und trifft heuristische Entscheidungen darüber, welche Aufrufe untersucht werden sollen (darüber hinaus sind einige Aufrufe über Übersetzungseinheiten hinweg und für den Analyzer unsichtbar). In unserem Fall erfordert unsere Definition von Korrektheit vollständige Informationen. Daher müssen wir die Prototypen aller Funktionsaufrufe mit den Informationen annotieren, die die Analyse benötigt, auch wenn diese Informationen ansonsten durch interprozedurale statische Analyse verfügbar wären.

Glücklicherweise können wir jedoch diese interprozedurale Analyse weiterhin nutzen, um sicherzustellen, dass die Annotationen, die wir auf einer bestimmten Funktion platzieren, tatsächlich korrekt sind, gegeben die Implementierung dieser Funktion.

## The analyzer annotations

Diese Anmerkungen sind in src/support/analyzer_annotations.h zu finden. Sie sind nur aktiv, wenn der Analyzer verwendet wird, und erweitern sich entweder zu nichts (für Prototyp-Anmerkungen) oder zu No-Op-Anweisungen (für funktionsähnliche Anmerkungen).

### `JL_NOTSAFEPOINT`

Dies ist vielleicht die häufigste Annotation und sollte auf jede Funktion angewendet werden, von der bekannt ist, dass sie nicht zu einem GC-Sicherheitspunkt führen kann. Im Allgemeinen ist es nur sicher, dass eine solche Funktion arithmetische Operationen, Speicherzugriffe und Aufrufe von Funktionen durchführt, die entweder mit `JL_NOTSAFEPOINT` annotiert sind oder anderweitig bekannt sind, dass sie keine Sicherheitsstellen sind (z. B. Funktionen in der C-Standardbibliothek, die im Analyzer fest codiert sind).

Es ist gültig, Werte über Aufrufe an jede Funktion, die mit diesem Attribut annotiert ist, ungerootet zu halten:

Verwendungsbeispiel:

```c
void jl_get_one() JL_NOTSAFEPOINT {
  return 1;
}

jl_value_t *example() {
  jl_value_t *val = jl_alloc_whatever();
  // This is valid, even though `val` is unrooted, because
  // jl_get_one is not a safepoint
  jl_get_one();
  return val;
}
```

### `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY`

Wenn `JL_MAYBE_UNROOTED` als Argument in einer Funktion annotiert ist, bedeutet dies, dass dieses Argument übergeben werden kann, auch wenn es nicht verwurzelt ist. Im normalen Verlauf der Ereignisse garantiert die Julia-ABI, dass Aufrufer Werte verwurzeln, bevor sie sie an Aufgerufene übergeben. Einige Funktionen halten sich jedoch nicht an diese ABI und erlauben es, Werte an sie zu übergeben, auch wenn sie nicht verwurzelt sind. Beachten Sie jedoch, dass dies nicht automatisch impliziert, dass das betreffende Argument erhalten bleibt. Die Annotation `ROOTS_TEMPORARILY` bietet die stärkere Garantie, dass der Wert nicht nur unverwurzelt übergeben werden kann, sondern auch über alle internen Safepoints des Aufgerufenen hinweg erhalten bleibt.

Beachten Sie, dass `JL_NOTSAFEPOINT` im Wesentlichen `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY` impliziert, da die Verwurzelung eines Arguments irrelevant ist, wenn die Funktion keine Safepoints enthält.

Ein zusätzlicher Punkt, den man beachten sollte, ist, dass diese Anmerkungen sowohl auf der Aufrufer- als auch auf der Aufgerufenen-Seite gelten. Auf der Aufrufer-Seite heben sie die normalerweise für Julia ABI-Funktionen erforderlichen Wurzelbeschränkungen auf. Auf der Aufgerufenen-Seite haben sie den gegenteiligen Effekt, dass diese Argumente nicht als implizit verwurzelt betrachtet werden.

Wenn eine dieser Anmerkungen auf die Funktion als Ganzes angewendet wird, gilt sie für alle Argumente der Funktion. Dies sollte im Allgemeinen nur für varargs-Funktionen erforderlich sein.

Verwendungsbeispiel:

```c
JL_DLLEXPORT void JL_NORETURN jl_throw(jl_value_t *e JL_MAYBE_UNROOTED);
jl_value_t *jl_alloc_error();

void example() {
  // The return value of the allocation is unrooted. This would normally
  // be an error, but is allowed because of the above annotation.
  jl_throw(jl_alloc_error());
}
```

### `JL_PROPAGATES_ROOT`

Diese Annotation wird häufig bei Zugriffsfunktionen gefunden, die ein verwurzelbares Objekt zurückgeben, das in einem anderen gespeichert ist. Wenn sie auf ein Funktionsargument angewendet wird, teilt sie dem Analyzer mit, dass die Wurzel für dieses Argument auch für den von der Funktion zurückgegebenen Wert gilt.

Verwendungsbeispiel:

```c
jl_value_t *jl_svecref(jl_svec_t *t JL_PROPAGATES_ROOT, size_t i) JL_NOTSAFEPOINT;

size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_svecref(svec, 1)
  // This is valid, because, as annotated by the PROPAGATES_ROOT annotation,
  // jl_svecref propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_ROOTING_ARGUMENT`/`JL_ROOTED_ARGUMENT`

Dies ist im Wesentlichen das Gegenstück zur Zuweisung von `JL_PROPAGATES_ROOT`. Wenn einem Feld eines anderen Wertes, der bereits verwurzelt ist, ein Wert zugewiesen wird, erbt der zugewiesene Wert die Wurzel des Wertes, in den er zugewiesen wird.

Verwendungsbeispiel:

```c
void jl_svecset(void *t JL_ROOTING_ARGUMENT, size_t i, void *x JL_ROOTED_ARGUMENT) JL_NOTSAFEPOINT


size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_box_long(10000);
  jl_svecset(svec, val);
  // This is valid, because the annotations imply that the
  // jl_svecset propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_GC_DISABLED`

Diese Annotation impliziert, dass diese Funktion nur mit deaktiviertem GC-Laufzeit aufgerufen wird. Funktionen dieser Art werden am häufigsten während des Starts und im GC-Code selbst angetroffen. Beachten Sie, dass diese Annotation gegen die Aufrufe zum Aktivieren/Deaktivieren der Laufzeit überprüft wird, sodass clang weiß, ob Sie lügen. Dies ist keine gute Möglichkeit, die Verarbeitung einer bestimmten Funktion zu deaktivieren, wenn der GC tatsächlich nicht deaktiviert ist (verwenden Sie `ifdef __clang_analyzer__`, wenn Sie das unbedingt müssen).

Verwendungsbeispiel:

```c
void jl_do_magic() JL_GC_DISABLED {
  // Wildly allocate here with no regard for roots
}

void example() {
  int en = jl_gc_enable(0);
  jl_do_magic();
  jl_gc_enable(en);
}
```

### `JL_REQUIRE_ROOTED_SLOT`

Diese Annotation erfordert, dass der Aufrufer einen Slot übergibt, der verwurzelt ist (d.h. Werte, die diesem Slot zugewiesen werden, werden verwurzelt).

Verwendungsbeispiel:

```c
void jl_do_processing(jl_value_t **slot JL_REQUIRE_ROOTED_SLOT) {
  *slot = jl_box_long(1);
  // Ok, only, because the slot was annotated as rooting
  jl_gc_safepoint();
}

void example() {
  jl_value_t *slot = NULL;
  JL_GC_PUSH1(&slot);
  jl_do_processing(&slot);
  JL_GC_POP();
}
```

### `JL_GLOBALLY_ROOTED`

Diese Annotation impliziert, dass ein gegebener Wert immer global verankert ist. Sie kann auf die Deklarationen globaler Variablen angewendet werden, in diesem Fall gilt sie für den Wert dieser Variablen (oder Werte, wenn die Deklaration für ein Array ist), oder auf Funktionen, in diesem Fall gilt sie für den Rückgabewert solcher Funktionen (z. B. für Funktionen, die immer einen privaten, global verankerten Wert zurückgeben).

Verwendungsbeispiel:

```
extern JL_DLLEXPORT jl_datatype_t *jl_any_type JL_GLOBALLY_ROOTED;
jl_ast_context_t *jl_ast_ctx(fl_context_t *fl) JL_GLOBALLY_ROOTED;
```

### `JL_ALWAYS_LEAFTYPE`

Diese Annotation ist im Wesentlichen äquivalent zu `JL_GLOBALLY_ROOTED`, sollte jedoch nur verwendet werden, wenn diese Werte aufgrund ihrer Eigenschaft als Blatttyp global verankert sind. Die Verankerung von Blatttypen ist etwas kompliziert. Sie sind im Allgemeinen über das `cache`-Feld des entsprechenden `TypeName` verankert, das selbst durch das enthaltende Modul verankert ist (d.h. sie sind verankert, solange das enthaltende Modul in Ordnung ist), und wir können im Allgemeinen davon ausgehen, dass Blatttypen dort verankert sind, wo sie verwendet werden. Wir können jedoch diese Eigenschaft in Zukunft verfeinern, sodass die separate Annotation hilft, den Grund für die globale Verankerung zu trennen.

Der Analyzer erkennt auch automatisch Überprüfungen auf die Blattart und wird sich nicht über fehlende GC-Wurzeln auf diesen Pfaden beschweren.

```
JL_DLLEXPORT jl_value_t *jl_apply_array_type(jl_value_t *type, size_t dim) JL_ALWAYS_LEAFTYPE;
```

### `JL_GC_PROMISE_ROOTED`

Dies ist eine funktionsähnliche Annotation. Jeder Wert, der an diese Annotation übergeben wird, wird für den Geltungsbereich der aktuellen Funktion als verwurzelt betrachtet. Sie ist als Ausweg für die Unzulänglichkeiten des Analyzers oder komplizierte Situationen gedacht. Sie sollte jedoch sparsam verwendet werden, zugunsten der Verbesserung des Analyzers selbst.

```
void example() {
  jl_value_t *val = jl_alloc_something();
  if (some_condition) {
    // We happen to know for complicated external reasons
    // that val is rooted under these conditions
    JL_GC_PROMISE_ROOTED(val);
  }
}
```

## Completeness of analysis

Der Analyzer betrachtet nur lokale Informationen. Insbesondere geht er im obigen Fall `PROPAGATES_ROOT` davon aus, dass solcher Speicher nur auf Arten modifiziert wird, die er sehen kann, nicht in aufgerufenen Funktionen (es sei denn, er entscheidet sich zufällig, diese in seine Analyse einzubeziehen) und nicht in gleichzeitig laufenden Threads. Daher kann es sein, dass er einige problematische Fälle übersieht, obwohl solche gleichzeitigen Modifikationen in der Praxis recht selten sind. Die Verbesserung des Analyzers, um mehr solcher Fälle zu behandeln, könnte ein interessantes Thema für zukünftige Arbeiten sein.
