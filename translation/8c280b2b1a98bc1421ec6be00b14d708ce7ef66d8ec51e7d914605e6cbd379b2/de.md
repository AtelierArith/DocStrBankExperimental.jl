```
LibGit2.Buffer
```

Ein Datenpuffer zum Exportieren von Daten aus libgit2. Entspricht der [`git_buf`](https://libgit2.org/libgit2/#HEAD/type/git_buf) Struktur.

Beim Abrufen von Daten aus LibGit2 würde eine typische Verwendung wie folgt aussehen:

```julia
buf_ref = Ref(Buffer())
@check ccall(..., (Ptr{Buffer},), buf_ref)
# Operation auf buf_ref
free(buf_ref)
```

Insbesondere ist zu beachten, dass `LibGit2.free` anschließend auf dem `Ref`-Objekt aufgerufen werden sollte.
