```
LibGit2.StrArrayStruct
```

Eine LibGit2-Darstellung eines Arrays von Zeichenfolgen. Entspricht der [`git_strarray`](https://libgit2.org/libgit2/#HEAD/type/git_strarray) Struktur.

Beim Abrufen von Daten aus LibGit2 würde eine typische Verwendung wie folgt aussehen:

```julia
sa_ref = Ref(StrArrayStruct())
@check ccall(..., (Ptr{StrArrayStruct},), sa_ref)
res = convert(Vector{String}, sa_ref[])
free(sa_ref)
```

Insbesondere ist zu beachten, dass `LibGit2.free` anschließend auf dem `Ref`-Objekt aufgerufen werden sollte.

Umgekehrt ist es beim Übergeben eines Vektors von Zeichenfolgen an LibGit2 im Allgemeinen am einfachsten, sich auf die implizite Konvertierung zu verlassen:

```julia
strs = String[...]
@check ccall(..., (Ptr{StrArrayStruct},), strs)
```

Beachten Sie, dass kein Aufruf von `free` erforderlich ist, da die Daten von Julia zugewiesen werden.
