```
Threads.threadid() -> Int
```

Holen Sie sich die ID-Nummer des aktuellen Ausführungsthreads. Der Master-Thread hat die ID `1`.

# Beispiele

```julia-repl
julia> Threads.threadid()
1

julia> Threads.@threads for i in 1:4
          println(Threads.threadid())
       end
4
2
5
4
```

!!! Hinweis     Der Thread, auf dem eine Aufgabe ausgeführt wird, kann sich ändern, wenn die Aufgabe yieldet, was als [`Task Migration`](@ref man-task-migration) bekannt ist. Aus diesem Grund ist es in den meisten Fällen nicht sicher, `threadid()` zu verwenden, um beispielsweise auf einen Vektor von Puffern oder zustandsbehafteten Objekten zuzugreifen.
