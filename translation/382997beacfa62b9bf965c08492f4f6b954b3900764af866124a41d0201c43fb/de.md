```
Base.@assume_effects Einstellung... [ex]
```

Überschreiben Sie das Effektmodell des Compilers. Dieses Makro kann in mehreren Kontexten verwendet werden:

1. Unmittelbar vor einer Methodendefinition, um das gesamte Effektmodell der angewendeten Methode zu überschreiben.
2. Innerhalb eines Funktionskörpers ohne Argumente, um das gesamte Effektmodell der umschließenden Methode zu überschreiben.
3. Auf einen Codeblock angewendet, um das lokale Effektmodell des angewendeten Codeblocks zu überschreiben.

# Beispiele

```jldoctest
julia> Base.@assume_effects :terminates_locally function fact(x)
           # Verwendung 1:
           # dieses :terminates_locally erlaubt es, `fact` konstant zu falten
           res = 1
           0 ≤ x < 20 || error("schlechte fakt")
           while x > 1
               res *= x
               x -= 1
           end
           return res
       end
fact (generische Funktion mit 1 Methode)

julia> code_typed() do
           fact(12)
       end |> only
CodeInfo(
1 ─     return 479001600
) => Int64

julia> code_typed() do
           map((2,3,4)) do x
               # Verwendung 2:
               # dieses :terminates_locally erlaubt es, diese anonyme Funktion konstant zu falten
               Base.@assume_effects :terminates_locally
               res = 1
               0 ≤ x < 20 || error("schlechte fakt")
               while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}

julia> code_typed() do
           map((2,3,4)) do x
               res = 1
               0 ≤ x < 20 || error("schlechte fakt")
               # Verwendung 3:
               # mit dieser :terminates_locally Annotation überspringt der Compiler das Tainting
               # des `:terminates` Effekts innerhalb dieses `while` Blocks, was es der übergeordneten
               # anonymen Funktion ermöglicht, konstant gefaltet zu werden
               Base.@assume_effects :terminates_locally while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}
```

!!! compat "Julia 1.8"
    Die Verwendung von `Base.@assume_effects` erfordert Julia Version 1.8.


!!! compat "Julia 1.10"
    Die Verwendung innerhalb eines Funktionskörpers erfordert mindestens Julia 1.10.


!!! compat "Julia 1.11"
    Die Annotation des Codeblocks erfordert mindestens Julia 1.11.


!!! warning
    Unsachgemäße Verwendung dieses Makros führt zu undefiniertem Verhalten (einschließlich Abstürzen, falschen Antworten oder anderen schwer nachverfolgbaren Fehlern). Verwenden Sie es mit Vorsicht und nur als letztes Mittel, wenn es unbedingt erforderlich ist. Selbst in einem solchen Fall sollten Sie alle möglichen Schritte unternehmen, um die Stärke der Effektbehauptung zu minimieren (z. B. verwenden Sie nicht `:total`, wenn `:nothrow` ausreichend gewesen wäre).


Im Allgemeinen macht jeder `setting` Wert eine Behauptung über das Verhalten der Funktion, ohne dass der Compiler beweisen muss, dass dieses Verhalten tatsächlich wahr ist. Diese Behauptungen gelten für alle Weltalter. Es ist daher ratsam, die Verwendung generischer Funktionen zu begrenzen, die später erweitert werden könnten, um die Annahme zu ungültig zu machen (was zu undefiniertem Verhalten führen würde).

Die folgenden `setting`s werden unterstützt.

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:terminates_locally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:noub_if_noinbounds`
  * `:nortcall`
  * `:foldable`
  * `:removable`
  * `:total`

# Erweiterte Hilfe

---

## `:consistent`

Die `:consistent` Einstellung behauptet, dass für gleichwertige (`===`) Eingaben:

  * Die Art der Beendigung (Rückgabewert, Ausnahme, Nichtbeendigung) immer gleich sein wird.
  * Wenn die Methode zurückgibt, werden die Ergebnisse immer gleichwertig sein.

!!! note
    Dies impliziert insbesondere, dass die Methode kein frisch zugewiesenes veränderliches Objekt zurückgeben darf. Mehrfache Zuweisungen von veränderlichen Objekten (auch mit identischem Inhalt) sind nicht gleichwertig.


!!! note
    Die `:consistent`-cy Behauptung wird weltalterweise gemacht. Formell schreiben wir $fᵢ$ für die Auswertung von $f$ im Weltalter $i$, dann erfordert diese Einstellung:

    $$
    ∀ i, x, y: x ≡ y → fᵢ(x) ≡ fᵢ(y)
    $$

    Für zwei Weltalter $i$, $j$ mit $i ≠ j$ kann es jedoch sein, dass $fᵢ(x) ≢ fⱼ(y)$.

    Eine weitere Implikation ist, dass `:consistent` Funktionen ihren Rückgabewert nicht von dem Zustand des Heaps oder einem anderen globalen Zustand abhängig machen dürfen, der für ein gegebenes Weltalter nicht konstant ist.


!!! note
    Die `:consistent`-cy umfasst alle legalen Umformulierungen, die vom Optimierer durchgeführt werden. Beispielsweise werden Floating-Point-Fastmath-Operationen nicht als `:consistent` betrachtet, da der Optimierer sie umformulieren kann, was dazu führt, dass die Ausgabe nicht `:consistent` ist, selbst für dasselbe Weltalter (z. B. weil eine im Interpreter ausgeführt wurde, während die andere optimiert wurde).


!!! note
    Wenn `:consistent` Funktionen durch das Auslösen einer Ausnahme beendet werden, ist diese Ausnahme selbst nicht erforderlich, um die oben angegebene Gleichwertigkeitsanforderung zu erfüllen.


---

## `:effect_free`

Die `:effect_free` Einstellung behauptet, dass die Methode frei von extern sichtbar semantischen Nebenwirkungen ist. Die folgende Liste ist unvollständig und umfasst extern sichtbar semantische Nebenwirkungen:

  * Ändern des Wertes einer globalen Variablen.
  * Mutieren des Heaps (z. B. eines Arrays oder veränderlichen Wertes), es sei denn, wie unten angegeben.
  * Ändern der Methodentabelle (z. B. durch Aufrufe von eval).
  * Datei-/Netzwerk-/usw. I/O.
  * Aufgabenwechsel.

Es sind jedoch die folgenden explizit nicht semantisch sichtbar, auch wenn sie beobachtbar sein können:

  * Speicherzuweisungen (sowohl veränderlich als auch unveränderlich).
  * Verstrichene Zeit.
  * Garbage Collection.
  * Heap-Mutationen von Objekten, deren Lebensdauer die Methode nicht überschreitet (d. h. die in der Methode zugewiesen wurden und nicht entkommen).
  * Der zurückgegebene Wert (der extern sichtbar ist, aber keine Nebenwirkung darstellt).

Die Faustregel hier ist, dass eine extern sichtbare Nebenwirkung alles ist, was die Ausführung des Rests des Programms beeinflussen würde, wenn die Funktion nicht ausgeführt wird.

!!! note
    Die `:effect_free` Behauptung gilt sowohl für die Methode selbst als auch für jeden Code, der von der Methode ausgeführt wird. Beachten Sie, dass die Behauptung für alle Weltalter gültig sein muss und die Verwendung dieser Behauptung entsprechend begrenzt werden sollte.


---

## `:nothrow`

Die `:nothrow` Einstellungen behaupten, dass diese Methode keine Ausnahme auslöst (d. h. entweder immer einen Wert zurückgibt oder niemals zurückgibt).

!!! note
    Es ist zulässig, dass mit `:nothrow` annotierte Methoden intern Ausnahmebehandlung verwenden, solange die Ausnahme nicht aus der Methode selbst erneut ausgelöst wird.


!!! note
    Wenn die Ausführung einer Methode `MethodError`s und ähnliche Ausnahmen auslösen kann, wird die Methode nicht als `:nothrow` betrachtet. Beachten Sie jedoch, dass umgebungsabhängige Fehler wie `StackOverflowError` oder `InterruptException` von diesem Effekt nicht modelliert werden und eine Methode, die zu `StackOverflowError` führen kann, daher nicht unbedingt `!:nothrow` sein muss (obwohl sie normalerweise auch `!:terminates` sein sollte).


---

## `:terminates_globally`

Die `:terminates_globally` Einstellungen behaupten, dass diese Methode schließlich beendet wird (entweder normal oder abnormal), d. h. nicht unendlich schleifen wird.

!!! note
    Diese `:terminates_globally` Behauptung umfasst alle anderen Methoden, die von der annotierten Methode aufgerufen werden.


!!! note
    Der Compiler wird dies als starke Indikation betrachten, dass die Methode relativ *schnell* beendet wird und kann (wenn sonst legal) diese Methode zur Compile-Zeit aufrufen. Es ist also eine schlechte Idee, diese Einstellung auf eine Methode zu annotieren, die *technisch*, aber nicht *praktisch* beendet.


---

## `:terminates_locally`

Die `:terminates_locally` Einstellung ist wie `:terminates_globally`, außer dass sie nur auf den syntaktischen Kontrollfluss *innerhalb* der annotierten Methode angewendet wird. Es ist daher eine viel schwächere (und damit sicherere) Behauptung, die die Möglichkeit der Nichtbeendigung zulässt, wenn die Methode eine andere Methode aufruft, die nicht beendet.

!!! note
    `:terminates_globally` impliziert `:terminates_locally`.


---

## `:notaskstate`

Die `:notaskstate` Einstellung behauptet, dass die Methode den lokalen Aufgabenstatus (task local storage, RNG-Zustand usw.) nicht verwendet oder ändert und daher sicher zwischen Aufgaben verschoben werden kann, ohne beobachtbare Ergebnisse.

!!! note
    Die Implementierung der Ausnahmebehandlung verwendet den Status, der im Aufgabenobjekt gespeichert ist. Dieser Status wird jedoch derzeit nicht im Rahmen von `:notaskstate` betrachtet und separat mit dem Effekt `:nothrow` verfolgt.


!!! note
    Die `:notaskstate` Behauptung betrifft den Zustand der *derzeit laufenden Aufgabe*. Wenn ein Verweis auf ein `Task`-Objekt auf andere Weise erhalten wird, die nicht berücksichtigt, welche Aufgabe *derzeit* läuft, muss der `:notaskstate` Effekt nicht getäuscht werden. Dies gilt selbst dann, wenn das genannte Aufgabenobjekt zufällig `===` zur derzeit laufenden Aufgabe ist.


!!! note
    Der Zugriff auf den Aufgabenstatus führt normalerweise auch zu einer Täuschung anderer Effekte, wie `:effect_free` (wenn der Aufgabenstatus geändert wird) oder `:consistent` (wenn der Aufgabenstatus in die Berechnung des Ergebnisses einfließt). Insbesondere kann Code, der nicht `:notaskstate` ist, aber `:effect_free` und `:consistent` ist, dennoch als toter Code eliminiert werden und somit zu `:total` befördert werden.


---

## `:inaccessiblememonly`

Die `:inaccessiblememonly` Einstellung behauptet, dass die Methode keinen extern zugänglichen veränderlichen Speicher verwendet oder ändert. Das bedeutet, dass die Methode auf veränderlichen Speicher für neu zugewiesene Objekte zugreifen oder diesen ändern kann, der von anderen Methoden oder der obersten Ausführung vor der Rückkehr aus der Methode nicht zugänglich ist, aber sie kann keinen veränderlichen globalen Zustand oder veränderlichen Speicher, auf den durch ihre Argumente verwiesen wird, verwenden oder ändern.

!!! note
    Unten ist eine unvollständige Liste von Beispielen, die diese Annahme ungültig machen:

      * ein globaler Verweis oder `getglobal` Aufruf, um auf eine veränderliche globale Variable zuzugreifen
      * eine globale Zuweisung oder `setglobal!` Aufruf, um eine Zuweisung an eine nicht konstante globale Variable durchzuführen
      * `setfield!` Aufruf, der ein Feld einer globalen veränderlichen Variable ändert


!!! note
    Diese `:inaccessiblememonly` Behauptung umfasst alle anderen Methoden, die von der annotierten Methode aufgerufen werden.


---

## `:noub`

Die `:noub` Einstellung behauptet, dass die Methode kein undefiniertes Verhalten ausführen wird (für irgendeine Eingabe). Beachten Sie, dass undefiniertes Verhalten technisch die Methode dazu bringen kann, gegen andere Effektbehauptungen (wie `:consistent` oder `:effect_free`) zu verstoßen, aber wir modellieren dies nicht, und sie setzen das Fehlen von undefiniertem Verhalten voraus.

---

## `:nortcall`

Die `:nortcall` Einstellung behauptet, dass die Methode `Core.Compiler.return_type` nicht aufruft und dass auch keine anderen Methoden, die diese Methode aufrufen könnte, `Core.Compiler.return_type` aufrufen.

!!! note
    Um genau zu sein, kann diese Behauptung verwendet werden, wenn ein Aufruf zu `Core.Compiler.return_type` zur Laufzeit nicht erfolgt; das heißt, wenn das Ergebnis von `Core.Compiler.return_type` genau zur Compile-Zeit bekannt ist und der Aufruf vom Optimierer eliminiert wird. Da jedoch davon abhängt, ob das Ergebnis von `Core.Compiler.return_type` zur Compile-Zeit gefaltet wird, stark von der Implementierung des Compilers abhängt, ist es im Allgemeinen riskant, dies zu behaupten, wenn die betreffende Methode `Core.Compiler.return_type` in irgendeiner Form verwendet.


---

## `:foldable`

Diese Einstellung ist eine praktische Abkürzung für die Menge von Effekten, die der Compiler garantieren muss, um einen Aufruf zur Compile-Zeit konstant zu falten. Sie ist derzeit äquivalent zu den folgenden `setting`s:

  * `:consistent`
  * `:effect_free`
  * `:terminates_globally`
  * `:noub`
  * `:nortcall`

!!! note
    Diese Liste umfasst insbesondere nicht `:nothrow`. Der Compiler wird weiterhin versuchen, die Konstantenpropagation durchzuführen und alle geworfenen Fehler zur Compile-Zeit zu notieren. Beachten Sie jedoch, dass gemäß den Anforderungen der `:consistent`-cy jeder solche annotierte Aufruf konsistent werfen muss, wenn die gleichen Argumentwerte verwendet werden.


!!! note
    Eine explizite `@inbounds` Annotation innerhalb der Funktion deaktiviert ebenfalls die konstante Faltung und wird nicht durch `:foldable` überschrieben.


---

## `:removable`

Diese Einstellung ist eine praktische Abkürzung für die Menge von Effekten, die der Compiler garantieren muss, um einen Aufruf, dessen Ergebnis zur Compile-Zeit nicht verwendet wird, zu löschen. Sie ist derzeit äquivalent zu den folgenden `setting`s:

  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`

---

## `:total`

Diese `setting` ist die maximal mögliche Menge von Effekten. Sie impliziert derzeit die folgenden anderen `setting`s:

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:nortcall`

!!! warning
    `:total` ist eine sehr starke Behauptung und wird wahrscheinlich in zukünftigen Versionen von Julia zusätzliche Semantiken gewinnen (z. B. wenn zusätzliche Effekte hinzugefügt und in die Definition von `:total` aufgenommen werden). Daher sollte es mit Vorsicht verwendet werden. Wann immer möglich, ziehen Sie es vor, die minimal mögliche Menge spezifischer Effektbehauptungen zu verwenden, die für eine bestimmte Anwendung erforderlich sind. In Fällen, in denen eine große Anzahl von Effektüberschreibungen auf eine Menge von Funktionen zutrifft, wird empfohlen, ein benutzerdefiniertes Makro anstelle der Verwendung von `:total` zu verwenden.


---

## Negierte Effekte

Effektnamen können mit `!` vorangestellt werden, um anzuzeigen, dass der Effekt aus einem früheren Metaeffekt entfernt werden sollte. Zum Beispiel bedeutet `:total !:nothrow`, dass der Aufruf im Allgemeinen total ist, er jedoch möglicherweise eine Ausnahme auslöst.
