```
join([io::IO,] iterator [, delim [, last]])
```

Fügen Sie jeden `iterator` zu einem einzelnen String zusammen, indem Sie den angegebenen Trennzeichen (falls vorhanden) zwischen benachbarten Elementen einfügen. Wenn `last` angegeben ist, wird es anstelle von `delim` zwischen den letzten beiden Elementen verwendet. Jedes Element des `iterator` wird über `print(io::IOBuffer, x)` in einen String umgewandelt. Wenn `io` angegeben ist, wird das Ergebnis in `io` geschrieben, anstatt als `String` zurückgegeben zu werden.

# Beispiele

```jldoctest
julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"

julia> join([1,2,3,4,5])
"12345"
```
