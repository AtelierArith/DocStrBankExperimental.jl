```
bind(chnl::Channel, task::Task)
```

Assoziiere die Lebensdauer von `chnl` mit einer Aufgabe. `Channel` `chnl` wird automatisch geschlossen, wenn die Aufgabe endet. Jede nicht abgefangene Ausnahme in der Aufgabe wird an alle Wartenden auf `chnl` weitergegeben.

Das `chnl`-Objekt kann unabhängig vom Abschluss der Aufgabe explizit geschlossen werden. Beendete Aufgaben haben keinen Einfluss auf bereits geschlossene `Channel`-Objekte.

Wenn ein Kanal an mehrere Aufgaben gebunden ist, wird der erste, der beendet wird, den Kanal schließen. Wenn mehrere Kanäle an dieselbe Aufgabe gebunden sind, wird das Beenden der Aufgabe alle gebundenen Kanäle schließen.

# Beispiele

```jldoctest
julia> c = Channel(0);

julia> task = @async foreach(i->put!(c, i), 1:4);

julia> bind(c,task);

julia> for i in c
           @show i
       end;
i = 1
i = 2
i = 3
i = 4

julia> isopen(c)
false
```

```jldoctest
julia> c = Channel(0);

julia> task = @async (put!(c, 1); error("foo"));

julia> bind(c, task);

julia> take!(c)
1

julia> put!(c, 1);
ERROR: TaskFailedException
Stacktrace:
[...]
    nested task error: foo
[...]
```
