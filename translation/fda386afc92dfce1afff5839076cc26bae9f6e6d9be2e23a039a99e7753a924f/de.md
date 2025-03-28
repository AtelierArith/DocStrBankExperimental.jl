```
Base64EncodePipe(ostream)
```

Gibt einen neuen schreibgeschützten I/O-Stream zurück, der alle geschriebenen Bytes in base64-kodierte ASCII-Bytes umwandelt, die in `ostream` geschrieben werden. Das Aufrufen von [`close`](@ref) auf dem `Base64EncodePipe`-Stream ist notwendig, um die Kodierung abzuschließen (schließt jedoch nicht `ostream`).

# Beispiele

```jldoctest
julia> io = IOBuffer();

julia> iob64_encode = Base64EncodePipe(io);

julia> write(iob64_encode, "Hello!")
6

julia> close(iob64_encode);

julia> str = String(take!(io))
"SGVsbG8h"

julia> String(base64decode(str))
"Hello!"
```
