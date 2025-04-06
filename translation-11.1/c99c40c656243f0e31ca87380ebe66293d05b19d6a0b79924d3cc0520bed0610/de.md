```
wait([x])
```

Blockiere die aktuelle Aufgabe, bis ein Ereignis eintritt, abhängig von der Art des Arguments:

  * [`Channel`](@ref): Warte darauf, dass ein Wert zum Kanal hinzugefügt wird.
  * [`Condition`](@ref): Warte auf [`notify`](@ref) bei einer Bedingung und gib den `val`-Parameter zurück, der an `notify` übergeben wurde. Das Warten auf eine Bedingung ermöglicht zusätzlich das Übergeben von `first=true`, was dazu führt, dass der Wartende *zuerst* in der Reihe steht, um bei `notify` aufgeweckt zu werden, anstatt dem üblichen First-in-First-out-Verhalten zu folgen.
  * `Process`: Warte darauf, dass ein Prozess oder eine Prozesskette beendet wird. Das Feld `exitcode` eines Prozesses kann verwendet werden, um Erfolg oder Misserfolg zu bestimmen.
  * [`Task`](@ref): Warte darauf, dass eine `Task` abgeschlossen wird. Wenn die Aufgabe mit einer Ausnahme fehlschlägt, wird eine `TaskFailedException` (die die fehlgeschlagene Aufgabe umschließt) ausgelöst.
  * [`RawFD`](@ref): Warte auf Änderungen an einem Dateideskriptor (siehe das `FileWatching`-Paket).

Wenn kein Argument übergeben wird, blockiert die Aufgabe für einen undefinierten Zeitraum. Eine Aufgabe kann nur durch einen expliziten Aufruf von [`schedule`](@ref) oder [`yieldto`](@ref) neu gestartet werden.

Oft wird `wait` innerhalb einer `while`-Schleife aufgerufen, um sicherzustellen, dass eine wartende Bedingung erfüllt ist, bevor fortgefahren wird.
