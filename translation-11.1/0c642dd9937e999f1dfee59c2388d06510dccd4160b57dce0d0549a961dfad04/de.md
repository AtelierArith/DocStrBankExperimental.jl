```
isopen(object) -> Bool
```

Bestimmen Sie, ob ein Objekt - wie ein Stream oder Timer - noch nicht geschlossen ist. Sobald ein Objekt geschlossen ist, wird es niemals ein neues Ereignis erzeugen. Da ein geschlossener Stream jedoch möglicherweise noch Daten in seinem Puffer hat, verwenden Sie [`eof`](@ref), um die Möglichkeit zu überprüfen, Daten zu lesen. Verwenden Sie das `FileWatching`-Paket, um benachrichtigt zu werden, wenn ein Stream möglicherweise beschreibbar oder lesbar ist.

# Beispiele

```jldoctest
julia> io = open("my_file.txt", "w+");

julia> isopen(io)
true

julia> close(io)

julia> isopen(io)
false
```
