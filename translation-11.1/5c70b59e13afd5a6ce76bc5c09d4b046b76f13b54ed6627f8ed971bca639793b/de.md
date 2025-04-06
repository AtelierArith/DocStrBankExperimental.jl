```
lock(lock)
```

Erwerben Sie das `lock`, wenn es verfügbar wird. Wenn das Lock bereits von einer anderen Aufgabe/Thread gesperrt ist, warten Sie, bis es verfügbar wird.

Jedes `lock` muss durch ein [`unlock`](@ref) ausgeglichen werden.
