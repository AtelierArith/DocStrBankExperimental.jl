```
asyncmap(f, c...; ntasks=0, batch_size=nothing)
```

Verwendet mehrere gleichzeitige Aufgaben, um `f` über eine Sammlung (oder mehrere gleich lange Sammlungen) abzubilden. Bei mehreren Sammlungsargumenten wird `f` elementweise angewendet.

`ntasks` gibt die Anzahl der Aufgaben an, die gleichzeitig ausgeführt werden sollen. Abhängig von der Länge der Sammlungen werden, wenn `ntasks` nicht angegeben ist, bis zu 100 Aufgaben für die gleichzeitige Abbildung verwendet.

`ntasks` kann auch als Funktion ohne Argumente angegeben werden. In diesem Fall wird die Anzahl der parallel auszuführenden Aufgaben vor der Verarbeitung jedes Elements überprüft, und eine neue Aufgabe wird gestartet, wenn der Wert von `ntasks_func` größer ist als die aktuelle Anzahl der Aufgaben.

Wenn `batch_size` angegeben ist, wird die Sammlung im Batch-Modus verarbeitet. `f` muss dann eine Funktion sein, die ein `Vector` von Argument-Tupeln akzeptiert und ein Array von Ergebnissen zurückgibt. Der Eingangsvektor hat eine Länge von `batch_size` oder weniger.

Die folgenden Beispiele heben die Ausführung in verschiedenen Aufgaben hervor, indem sie die `objectid` der Aufgaben zurückgeben, in denen die Abbildungsfunktion ausgeführt wird.

Zuerst, mit undefiniertem `ntasks`, wird jedes Element in einer anderen Aufgabe verarbeitet.

```
julia> tskoid() = objectid(current_task());

julia> asyncmap(x->tskoid(), 1:5)
5-element Array{UInt64,1}:
 0x6e15e66c75c75853
 0x440f8819a1baa682
 0x9fb3eeadd0c83985
 0xebd3e35fe90d4050
 0x29efc93edce2b961

julia> length(unique(asyncmap(x->tskoid(), 1:5)))
5
```

Mit `ntasks=2` werden alle Elemente in 2 Aufgaben verarbeitet.

```
julia> asyncmap(x->tskoid(), 1:5; ntasks=2)
5-element Array{UInt64,1}:
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94

julia> length(unique(asyncmap(x->tskoid(), 1:5; ntasks=2)))
2
```

Mit definierter `batch_size` muss die Abbildungsfunktion geändert werden, um ein Array von Argument-Tupeln zu akzeptieren und ein Array von Ergebnissen zurückzugeben. `map` wird in der modifizierten Abbildungsfunktion verwendet, um dies zu erreichen.

```
julia> batch_func(input) = map(x->string("args_tuple: ", x, ", element_val: ", x[1], ", task: ", tskoid()), input)
batch_func (generic function with 1 method)

julia> asyncmap(batch_func, 1:5; ntasks=2, batch_size=2)
5-element Array{String,1}:
 "args_tuple: (1,), element_val: 1, task: 9118321258196414413"
 "args_tuple: (2,), element_val: 2, task: 4904288162898683522"
 "args_tuple: (3,), element_val: 3, task: 9118321258196414413"
 "args_tuple: (4,), element_val: 4, task: 4904288162898683522"
 "args_tuple: (5,), element_val: 5, task: 9118321258196414413"
```
