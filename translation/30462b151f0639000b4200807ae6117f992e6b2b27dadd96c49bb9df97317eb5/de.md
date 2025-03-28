lock(f::Function, l::Lockable)

Erwirbt das mit `l` verbundene Schloss, führt `f` mit dem gehaltenen Schloss aus und gibt das Schloss zurück, wenn `f` zurückkehrt. `f` erhält ein positionsbasiertes Argument: den von `l` umschlossenen Wert. Wenn das Schloss bereits von einer anderen Aufgabe/Thread gesperrt ist, wird gewartet, bis es verfügbar wird. Wenn diese Funktion zurückkehrt, wurde das `lock` freigegeben, sodass der Aufrufer nicht versuchen sollte, es zu `unlock`en.

!!! compat "Julia 1.11"
    Erfordert mindestens Julia 1.11.

