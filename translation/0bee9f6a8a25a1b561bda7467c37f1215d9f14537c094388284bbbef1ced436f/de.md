```
Threads.Condition([lock])
```

Eine threadsichere Version von [`Base.Condition`](@ref).

Um [`wait`](@ref) oder [`notify`](@ref) auf einem `Threads.Condition` aufzurufen, müssen Sie zuerst [`lock`](@ref) darauf aufrufen. Wenn `wait` aufgerufen wird, wird das Lock während des Blockierens atomar freigegeben und vor der Rückkehr von `wait` wieder erworben. Daher sieht die idiomatische Verwendung eines `Threads.Condition` `c` wie folgt aus:

```
lock(c)
try
    while !thing_we_are_waiting_for
        wait(c)
    end
finally
    unlock(c)
end
```

!!! compat "Julia 1.2"
    Diese Funktionalität erfordert mindestens Julia 1.2.

