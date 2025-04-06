```
invokelatest(f, args...; kwargs...)
```

Ruft `f(args...; kwargs...)` auf, garantiert jedoch, dass die aktuellste Methode von `f` ausgeführt wird. Dies ist in speziellen Umständen nützlich, z. B. in langlaufenden Ereignisschleifen oder Rückruffunktionen, die veraltete Versionen einer Funktion `f` aufrufen können. (Der Nachteil ist, dass `invokelatest` etwas langsamer ist als der direkte Aufruf von `f`, und der Typ des Ergebnisses kann vom Compiler nicht abgeleitet werden.)

!!! compat "Julia 1.9"
    Vor Julia 1.9 war diese Funktion nicht exportiert und wurde als `Base.invokelatest` aufgerufen.

