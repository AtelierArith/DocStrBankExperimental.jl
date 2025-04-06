```
skipchars(predicate, io::IO; linecomment=nothing)
```

Bewege den Stream `io` so, dass das nächste gelesene Zeichen das erste verbleibende ist, für das `predicate` `false` zurückgibt. Wenn das Schlüsselwort-Argument `linecomment` angegeben ist, werden alle Zeichen von diesem Zeichen bis zum Beginn der nächsten Zeile ignoriert.

# Beispiele

```jldoctest
julia> buf = IOBuffer("    text")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=1, mark=-1)

julia> skipchars(isspace, buf)
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=5, mark=-1)

julia> String(readavailable(buf))
"text"
```
