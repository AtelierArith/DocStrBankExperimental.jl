```
Channel{T=Any}(func::Function, size=0; taskref=nothing, spawn=false, threadpool=nothing)
```

Erstellt eine neue Aufgabe aus `func`, bindet sie an einen neuen Kanal vom Typ `T` und der Größe `size` und plant die Aufgabe, alles in einem einzigen Aufruf. Der Kanal wird automatisch geschlossen, wenn die Aufgabe endet.

`func` muss den gebundenen Kanal als einziges Argument akzeptieren.

Wenn Sie eine Referenz auf die erstellte Aufgabe benötigen, übergeben Sie ein `Ref{Task}`-Objekt über das Schlüsselwortargument `taskref`.

Wenn `spawn=true`, kann die für `func` erstellte `Task` parallel auf einem anderen Thread geplant werden, was dem Erstellen einer Aufgabe über [`Threads.@spawn`](@ref) entspricht.

Wenn `spawn=true` und das Argument `threadpool` nicht gesetzt ist, wird es standardmäßig auf `:default` gesetzt.

Wenn das Argument `threadpool` gesetzt ist (auf `:default` oder `:interactive`), impliziert dies, dass `spawn=true` und die neue Aufgabe im angegebenen Threadpool erstellt wird.

Gibt einen `Channel` zurück.

# Beispiele

```jldoctest
julia> chnl = Channel() do ch
           foreach(i -> put!(ch, i), 1:4)
       end;

julia> typeof(chnl)
Channel{Any}

julia> for i in chnl
           @show i
       end;
i = 1
i = 2
i = 3
i = 4
```

Referenzierung der erstellten Aufgabe:

```jldoctest
julia> taskref = Ref{Task}();

julia> chnl = Channel(taskref=taskref) do ch
           println(take!(ch))
       end;

julia> istaskdone(taskref[])
false

julia> put!(chnl, "Hello");
Hello

julia> istaskdone(taskref[])
true
```

!!! compat "Julia 1.3"
    Der Parameter `spawn=` wurde in Julia 1.3 hinzugefügt. Dieser Konstruktor wurde in Julia 1.3 hinzugefügt. In früheren Versionen von Julia verwendete Channel Schlüsselwortargumente, um `size` und `T` festzulegen, aber diese Konstruktoren sind veraltet.


!!! compat "Julia 1.9"
    Das Argument `threadpool=` wurde in Julia 1.9 hinzugefügt.


```jldoctest
julia> chnl = Channel{Char}(1, spawn=true) do ch
           for c in "hello world"
               put!(ch, c)
           end
       end
Channel{Char}(1) (2 items available)

julia> String(collect(chnl))
"hello world"
```
