```
Timer(callback::Function, delay; interval = 0)
```

Erstellen Sie einen Timer, der die Funktion `callback` bei jedem Ablauf des Timers ausführt.

Wartende Aufgaben werden geweckt und die Funktion `callback` wird nach einer anfänglichen Verzögerung von `delay` Sekunden aufgerufen, und dann wiederholt mit dem angegebenen `interval` in Sekunden. Wenn `interval` gleich `0` ist, wird der Callback nur einmal ausgeführt. Die Funktion `callback` wird mit einem einzelnen Argument aufgerufen, dem Timer selbst. Stoppen Sie einen Timer, indem Sie `close` aufrufen. Der `callback` kann möglicherweise ein letztes Mal ausgeführt werden, wenn der Timer bereits abgelaufen ist.

# Beispiele

Hier wird die erste Zahl nach einer Verzögerung von zwei Sekunden ausgegeben, dann werden die folgenden Zahlen schnell ausgegeben.

```julia-repl
julia> begin
           i = 0
           cb(timer) = (global i += 1; println(i))
           t = Timer(cb, 2, interval=0.2)
           wait(t)
           sleep(0.5)
           close(t)
       end
1
2
3
```
