# High-level Overview of the Native-Code Generation Process

## Representation of Pointers

Beim Ausgeben von Code in eine Objektdatei werden Zeiger als Relokationen ausgegeben. Der Deserialisierungscode stellt sicher, dass jedes Objekt, das auf eine dieser Konstanten zeigt, neu erstellt wird und den richtigen Laufzeitzeiger enthält.

Andernfalls werden sie als literale Konstanten ausgegeben.

Um eines dieser Objekte auszugeben, rufen Sie `literal_pointer_val` auf. Es kümmert sich um die Verfolgung des Julia-Werts und des LLVM-Globals und stellt sicher, dass sie sowohl zur aktuellen Laufzeit als auch nach der Deserialisierung gültig sind.

Wenn sie in die Objektdatei ausgegeben werden, werden diese Globals als Referenzen in einer großen `gvals`-Tabelle gespeichert. Dies ermöglicht es dem Deserialisierer, sie nach Index zu referenzieren und einen benutzerdefinierten manuellen Mechanismus ähnlich einer Global Offset Table (GOT) zu implementieren, um sie wiederherzustellen.

Funktionszeiger werden ähnlich behandelt. Sie werden als Werte in einer großen `fvals`-Tabelle gespeichert. Wie bei globalen Variablen ermöglicht dies dem Deserialisierer, sie über einen Index zu referenzieren.

Beachten Sie, dass `extern`-Funktionen separat behandelt werden, mit Namen, über den üblichen Symbolauflösungsmechanismus im Linker.

Beachten Sie auch, dass `ccall`-Funktionen ebenfalls separat behandelt werden, über eine manuelle GOT und eine Prozedurverknüpfungstabelle (PLT).

## Representation of Intermediate Values

Werte werden in einer `jl_cgval_t`-Struktur übergeben. Dies stellt einen R-Wert dar und enthält genügend Informationen, um zu bestimmen, wie er irgendwo zugewiesen oder übergeben werden kann.

Sie werden über einen der Hilfskonstruktoren erstellt, normalerweise: `mark_julia_type` (für unmittelbare Werte) und `mark_julia_slot` (für Zeiger auf Werte).

Die Funktion `convert_julia_type` kann zwischen beliebigen zwei Typen umwandeln. Sie gibt einen R-Wert zurück, bei dem `cgval.typ` auf `typ` gesetzt ist. Sie wird das Objekt in die angeforderte Darstellung umwandeln, indem sie Heap-Boxen erstellt, Stapelkopien anlegt und getaggte Vereinigungen berechnet, um die Darstellung zu ändern.

Im Gegensatz dazu wird `update_julia_type` `cgval.typ` nur dann in `typ` ändern, wenn dies ohne Kosten (d.h. ohne Code zu erzeugen) möglich ist.

## Union representation

Abgeleitete Unionstypen können über eine getaggte Typdarstellung im Stack zugewiesen werden.

Die primitiven Routinen, die in der Lage sein müssen, mit getaggten Vereinigungen umzugehen, sind:

  * mark-type
  * load-local
  * store-local
  * isa
  * ist
  * emit_typen
  * emit_sizeof
  * gekäst
  * unbox
  * spezialisiertes cc-ret

Alles andere sollte in der Inferenz mit diesen Primitiven zur Implementierung der Vereinigungsaufspaltung möglich sein.

Die Darstellung des getaggten Unions erfolgt als ein Paar von `< void* union, byte selector >`. Der Selektor hat eine feste Größe von `byte & 0x7f` und wird die ersten 126 isbits taggen. Er zeichnet die einsbasierte Tiefensuche in den Typ-Union der isbits-Objekte auf. Ein Index von null zeigt an, dass das `union*` tatsächlich ein getaggter, heap-allocierter `jl_value_t*` ist und als normales, verpacktes Objekt behandelt werden muss, anstatt als getaggter Union.

Das hohe Bit des Selektors (`byte & 0x80`) kann getestet werden, um festzustellen, ob der `void*` tatsächlich eine heap-allocierte (`jl_value_t*`) Box ist, wodurch die Kosten für die Neuzuordnung einer Box vermieden werden, während die Fähigkeit zur effizienten Handhabung von Union-Splittungen basierend auf den niedrigen Bits erhalten bleibt.

Es ist garantiert, dass `byte & 0x7f` ein exakter Test für den Typ ist. Wenn der Wert durch ein Tag dargestellt werden kann, wird er niemals als `byte = 0x80` markiert. Es ist nicht notwendig, auch den Typ-Tag zu testen, wenn `isa` getestet wird.

Der `union*`-Speicherbereich kann in *beliebiger* Größe zugewiesen werden. Die einzige Einschränkung besteht darin, dass er groß genug sein muss, um die derzeit durch `selector` angegebenen Daten zu enthalten. Möglicherweise ist er nicht groß genug, um die Vereinigung aller Typen zu enthalten, die dort gemäß dem zugehörigen Union-Typfeld gespeichert werden könnten. Seien Sie beim Kopieren entsprechend vorsichtig.

## Specialized Calling Convention Signature Representation

Ein `jl_returninfo_t`-Objekt beschreibt die Details der Aufrufkonvention eines beliebigen Aufrufbaren.

Wenn eines der Argumente oder der Rückgabewert einer Methode unboxed dargestellt werden kann und die Methode keine varargs ist, erhält sie eine optimierte Aufrufkonvention-Signatur basierend auf ihren `specTypes` und `rettype` Feldern.

Die allgemeinen Grundsätze sind, dass:

  * Primitive-Typen werden in int-/float-Register übergeben.
  * Tupel von VecElement-Typen werden in Vektorregistern übergeben.
  * Strukturen werden im Stack übergeben.
  * Rückgabewerte werden ähnlich wie Argumente behandelt, mit einer Größenobergrenze, ab der sie stattdessen über ein verborgenes sret-Argument zurückgegeben werden.

Die gesamte Logik dafür wird von `get_specsig_function` und `deserves_sret` implementiert.

Zusätzlich, wenn der Rückgabetyp eine Union ist, kann er als ein Paar von Werten (einen Zeiger und ein Tag) zurückgegeben werden. Wenn die Union-Werte im Stack zugewiesen werden können, wird auch ausreichend Platz, um sie zu speichern, als verstecktes erstes Argument übergeben. Es liegt am Aufgerufenen, ob der zurückgegebene Zeiger auf diesen Speicher, ein verpacktes Objekt oder sogar einen anderen konstanten Speicher zeigt.
